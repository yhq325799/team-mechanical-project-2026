# team-mechanical-project-2026

小组协作仓库，用于存放三人的 SolidWorks 机械设计文件（零件/装配体/工程图等）。所有 CAD 文件通过 **Git LFS** 管理，避免仓库膨胀。

## 目录结构

```
team-mechanical-project-2026/
├── yang_mechanical/   # 队长：杨
├── su_mechanical/     # 队员：苏
├── sun_mechanical/    # 队员：孙
├── .gitattributes  # LFS 规则（勿随意改动）
└── README.md
```

每个人只在自己的文件夹里提交文件，不要改动别人的文件夹。

---

## 首次使用（每人只需做一次）

### 1. 安装 Git LFS

确保已安装 Git LFS 命令行工具：

- Windows：下载安装 <https://git-lfs.com>，或运行 `winget install Git.LFS`
- 验证安装：`git lfs version` 能正常输出即可

### 2. 克隆仓库

```bash
git clone https://github.com/yhq325799/team-mechanical-project-2026.git
cd team-mechanical-project-2026
```

### 3. 初始化 LFS

```bash
git lfs install
```

> 说明：`.gitattributes` 已包含 LFS 规则，会**自动**把以下类型的文件交给 LFS 管理：
>
> - SolidWorks 原生：`.sldprt` `.sldasm` `.slddrw` `.sldblk` `.sldmat` `.sldfvt`
> - 导出/中性格式：`.step` `.stp` `.iges` `.igs` `.stl`

---

## 提交文件流程

1. 把 SolidWorks 文件（零件 `.sldprt`、装配体 `.sldasm`、工程图 `.slddrw`）复制到自己的文件夹，例如 `yang_mechanical/`。
   - **注意**：装配体 `.sldasm` 依赖的零件 `.sldprt` 也要一起提交，否则别人打开装配体会缺零件。

2. 提交：

```bash
git add yang_mechanical
git commit -m "添加装配体 xxx"
git pull --rebase
git push
```

3. 验证文件是否真的走 LFS（可选）：

```bash
git lfs ls-files
```

输出中文件名前带 `*` 表示已由 LFS 管理（例如 `abc123 * yang_mechanical/xxx.sldprt`）。

---

## 注意事项

- **先 pull 再 push**：协作时提交前务必先 `git pull --rebase`，避免冲突。
- **不要提交大文件的非 CAD 格式**：`.sldprt/.sldasm/.slddrw` 及上面列出的导出格式会走 LFS；其他超大二进制文件不要放进仓库。
- **GitHub LFS 配额**：免费账户每月约 1 GB 存储 / 1 GB 带宽，SolidWorks 文件较大，请只提交必要的最终文件，不要提交临时/备份文件。
- **文件损坏提示**：如果打开文件时 SolidWorks 提示损坏，通常是 LFS 未正确下载，运行 `git lfs pull` 即可。
