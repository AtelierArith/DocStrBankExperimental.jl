# LDPCStorage.jl

[![CI](https://github.com/XQP-Munich/LDPCStorage.jl/actions/workflows/CI.yml/badge.svg)](https://github.com/XQP-Munich/LDPCStorage.jl/actions) [![codecov](https://codecov.io/gh/XQP-Munich/LDPCStorage.jl/branch/main/graph/badge.svg?token=TGISS7YIJT)](https://codecov.io/gh/XQP-Munich/LDPCStorage.jl) [![License](https://img.shields.io/github/license/XQP-Munich/LDPCStorage.jl)](./LICENSE) [![Aqua QA](https://raw.githubusercontent.com/JuliaTesting/Aqua.jl/master/badge.svg)](https://github.com/JuliaTesting/Aqua.jl) [![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.5589595.svg)](https://doi.org/10.5281/zenodo.5589595)

*ゼロと1のみを含むスパース行列を保存するためのファイル形式を読み書きします。低密度パリティチェック（LDPC）行列での使用を意図しています。また、準周期的LDPCコードの効率的な保存もサポートしています。*

## インストール

[Julia](https://julialang.org/)を実行し、]を入力してJuliaのパッケージマネージャを表示し、パッケージを追加します：

```julia
julia> ]
(v1.9) pkg> add LDPCStorage
```

## サポートされているファイル形式

  * `alist` (David MacKayらによる、http://www.inference.org.uk/mackay/codes/alist.htmlを参照)
  * `cscmat` (カスタム形式) 廃止予定
  * `bincsc.json` (圧縮スパース列（CSC）に基づく。有効な`json`。)
  * `qccsc.json` (圧縮スパース列（CSC）に基づく。有効な`json`。準周期的LDPC行列の指数を保存)
  * `hpp (C++ヘッダー)` 行列のCSCを静的データとして（書き込み専用、読み取りはサポートされていません！）

## 使用方法

```julia
using SparseArrays
using LDPCStorage

H = sparse(Int8[
        0 0 1 1 0 0 0 0 1 0 0 1 1 0
        1 0 0 1 1 0 0 0 0 0 1 0 0 1
        0 1 0 1 0 1 1 0 1 0 0 1 1 0
        1 0 0 1 0 0 0 1 0 1 0 1 0 1
    ])

save_to_alist("./ldpc.alist", H)
H_alist = load_alist("./ldpc.alist")
H == H_alist || warn("失敗")

save_to_bincscjson("./ldpc.bincsc.json", H)
H_csc = load_ldpc_from_json("./ldpc.bincsc.json")
H == H_csc || warn("失敗")

open("./autogen_ldpc.hpp", "w+") do io
    print_cpp_header(io, H)
end
```

`IO`オブジェクトを受け入れるメソッドもあります：`print_alist`、`print_bincscjson`など。

いくつかのメソッドは準周期的指数を直接出力することをサポートしており、例えば、`print_cpp_header_QC`はC++ヘッダーを出力します。

## 貢献

貢献、機能リクエスト、提案を歓迎します。問題をオープンするか、直接お問い合わせください。
