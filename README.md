# OS大赛赛题协作文档

## 进度

| 题目 | 题目描述 | 编译方法 | 样例输出 | 评分依据 | 
| --- | --- | --- | --- | --- | 
| basic | :white_check_mark:| :white_check_mark: |:white_check_mark: | :white_check_mark: |
| busybox | :x: | :white_check_mark: | :x: | :white_check_mark: |
| lua | :x: | :white_check_mark: | :x: | :white_check_mark: |
| libctest | :x: | :white_check_mark: | :x: | :white_check_mark: |
| iozone | :x: | :white_check_mark: | :x: | :white_check_mark: |
| unixbench | :x: | :x: | :x: | :x: |
| iperf | :x: | :x: | :x: | :x: |
| libcbench | :x: | :x: | :x: | :x: |
| lmbench | :x: | :x: | :x: | :x: |
| netperf | :x: | :x: | :x: | :x: |
| cyclictest | :x: | :x: | :x: | :x: |
| ltp |:x: | :x: | :x: | :x: |

## 说明

本届操作系统大赛提供了basic、busybox、lua、libctest、iozone、unixbench、iperf、libcbench、lmbench、netperf、cyclictest和LTP共12组测试题目。

对上述每个测试题目，需给出题目描述、编译方法、样例输出、评分依据四个部分。

### 题目描述

描述此题目的基本内容和考察目标等信息。

### 编译方法

即如何通过源代码构建出符合大赛要求的二进制文件。本届大赛要求对每个题目编译出riscv-glibc、riscv-musl、loongarch-glibc、loongarch-musl 4组可执行文件，并将其放在比赛提供的磁盘镜像中供参赛学生使用。

使用不同体系结构平台和不同C运行时库进行编译时参数应尽可能相同，减少同一个题目在不同环境中的差异。

如果题目ELF文件运行时需要依赖动态链接库或其他磁盘文件（如libctest），请在构建脚本中将所需的文件一并复制到磁盘镜像中。

如果题目并非直接以二进制或Shell脚本启动（如LTP使用了基于Python的kirk），考虑到参赛队伍提交的OS不一定能支持完整的Python，因此需要对题目代码进行修改，使其能够以纯Shell脚本或二进制文件直接启动。

题目编译构建时应使用[赛题仓库](https://github.com/oscomp/testsuits-for-oskernel/tree/pre-2025)中提供的Docker镜像环境，并将此部分内容合并回仓库中。合并的内容包括：源代码、构建脚本（Makefile）、启动脚本（judge/xxxxx_testcode.sh）。

### 样例输出

大赛评分原理为：系统会捕获每一个测试题目的stdout，并根据此输出内容进行评分，因此需在文档中给出若干个有代表性的样例输出，并对其各部分含义做出解释，以便参赛队伍理解题目内容和目标。

### 评分依据

如何通过上述输出信息给出得分。例如在输出中匹配到什么信息即认为得分有效，应得多少分，对于性能测试样例给出的带宽、耗时等信息通过什么样的公式转换成最终得分。

评分脚本可参考本仓库judge目录下的文件，命名统一为judge_xxxxx.py。xxxxx为此测试题目的名称，只能为字母和数字，不能有连字符等其他符号。

### 其他

如有其他注意事项，请在文档中说明。如果现有条件不能满足题目运行，例如题目仓库中的公共环境（libc.so、链接器、文件系统结构等）不符合题目运行要求，Docker镜像中现有的工具不能编译出题目执行文件，网络相关的题目需要预先准备公共server等，请与我联系更新。
