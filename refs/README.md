# RIPPLE CPU 参考文献 / 资源清单

本目录存放 RIPPLE CPU PRD 中引用或依赖的核心外部资源，供后续实现、验证时核对事实依据，避免 AI 在编码时出现事实性错误。

## 1. RISC-V ISA 规范

| 资源文件 | 原始来源 | 说明 | 状态 |
|---|---|---|---|
| `riscv-unprivileged.pdf` | [RISC-V Unprivileged ISA Spec v20250508](https://github.com/riscv/riscv-isa-manual/releases) | 非特权指令集完整手册，包含 RV64I/M/A/F/D/C、Zfa、Zicond、Zicsr、Zicntr、B 扩展等全部已批准扩展 | 已下载 |
| `riscv-privileged.pdf` | [RISC-V Privileged ISA Spec v20250508](https://github.com/riscv/riscv-isa-manual/releases) | 特权架构手册：CSR、中断/异常、S-mode、VM、PMP、reset 等 | 已下载 |
| `riscv-v-spec-1.0.pdf` | [RISC-V "V" Vector Extension v1.0](https://github.com/riscv/riscv-v-spec/releases/download/v1.0/riscv-v-spec-1.0.pdf) | 向量扩展及 Zve32x/Zve32f/Zve64x/Zve64f/Zve64d 嵌入式向量子集 | 已下载 |
| `riscv-cmo.pdf` | [RISC-V CMO Spec v1.0.1](https://github.com/riscv/riscv-cmo) | Zicbom（cache-block 管理）、Zicbop（预取提示）、Zicboz（零化） | 已下载 |
| `riscv-debug-spec.pdf` | [RISC-V Debug Spec v1.0.0-rc1](https://github.com/riscv/riscv-debug-spec) | JTAG、DTM、DM、trigger module、halt/resume 等调试架构 | 已下载 |
| `zfa.md` | [docs.riscv.org Zfa 章节](https://docs.riscv.org/reference/isa/v20250508/unpriv/zfa.html) | 浮点附加指令 fli/fminm/fmaxm/fround/froundnx/fclass 等（HTML 转 Markdown） | 已转换 |
| `zicond.md` | [docs.riscv.org Zicond 章节](https://docs.riscv.org/reference/isa/v20250508/unpriv/zicond.html) | 整数条件置零 czero.eqz / czero.nez（HTML 转 Markdown） | 已转换 |

> 说明：`riscv-unprivileged.pdf` 已覆盖 Zfa / Zicond，但为避免大文档检索不便，额外将对应章节转换为 Markdown。

## 2. 分支预测器论文

| 资源文件 | 原始来源 | 说明 | 状态 |
|---|---|---|---|
| `tage-sc-l-cbp2016.pdf` | [CBP 2016: TAGE-SC-L Branch Predictors Again (André Seznec)](http://www.jilp.org/cbp2016/paper/AndreSeznecLimited.pdf) | PRD 主预测器基线：8 Tag 表 + Statistical Corrector + Loop Predictor | 已下载 |
| `ittage.pdf` | [A 64-Kbytes ITTAGE Indirect Branch Predictor (André Seznec, 2011)](https://www.jilp.org/jwac-2/program/cbp3_07_seznec.pdf) | 间接跳转目标预测器（ITAGE 变体） | 已下载 |
| `bullseye.pdf` | [Taming Wild Branches: Overcoming Hard-to-Predict Branches using the Bullseye Predictor (CBP 2025)](https://arxiv.org/pdf/2506.06773.pdf) | H2P 辅助预测器：HIT 表、Trial、抑制策略来源 | 已下载 |

## 3. 数据预取器论文

| 资源文件 | 原始来源 | 说明 | 状态 |
|---|---|---|---|
| `berti-dpc3.pdf` | [Berti: A Per-Page Best-Request-Time Delta Prefetcher (DPC 2022)](https://dpc3.compas.cs.stonybrook.edu/pdfs/Berti.pdf) | L1D 主预取器：per-page delta tracking | 已下载 |
| `bertigo.pdf` | [BertiGO: Context-Aware Local-Delta Prefetching (DPC 2026)](https://github.com/CMU-SAFARI/DPC4/raw/main/final-versions/BertiGO-final.pdf) | L2 预取器：多 PC 上下文、bitmap filter、Set-Dueling | 已下载 |

## 4. 参考开源项目（未下载代码仓库，仅记录链接）

PRD 中提到的开源/参考项目，主要用于性能对标或验证框架选型：

| 项目 | 链接 | 说明 |
|---|---|---|
| BOOM v3 | https://github.com/riscv-boom/riscv-boom | 开源高性能 RISC-V 核心，PRD 性能对比参考 |
| Difftest | https://github.com/OpenXiangShan/difftest | 处理器差分测试框架，PRD 验证框架参考 |
| Spike (RISC-V ISA Simulator) | https://github.com/riscv-software-src/riscv-isa-sim | 官方 RISC-V ISA 参考模型 |

## 5. 其他引用但未下载的资源

| 资源 | 未下载原因 | PRD 中位置 |
|---|---|---|
| AMBA AXI5 协议规范 | ARM 官方文档需注册/受版权保护，建议根据项目需要单独获取 | 第 10 章总线接口 |
| Ahead Pipelining (1995 ISCA) | PRD 仅作为历史学术来源提及，未给出具体论文标题/DOI；若后续实现 branch predictor 的 ahead-pipelining 结构，可再补充 | 5.1.3 节 |

## 6. 校验说明

- 所有 PDF 均通过 `file` 命令验证为有效 PDF。
- HTML 转 Markdown 使用 `markdownify` 完成，保留章节结构和表格。
- 如果后续 PRD 版本新增引用，应继续补充到本目录并更新本清单。
