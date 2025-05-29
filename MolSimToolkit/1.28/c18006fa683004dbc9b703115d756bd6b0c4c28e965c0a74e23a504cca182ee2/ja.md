```
remd_data(log::String)
```

Gromacsで実行された(H)REMDシミュレーションからログファイルを読み込むための関数です。

交換が試みられたステップ、交換行列、および確率行列を含む`GromacsREMDlog`構造体を返します。交換行列は、各ステップの各摂動レベルでのレプリカ番号を含みます。確率行列は、各レプリカが各レベルに存在する確率を含みます。

Gromacsのバージョンでログファイルをテストしました:      - 2019.4     - 5.0.4

# 例

まず、ログファイルからREMDデータを取得します:

```julia-repl
julia> using MolSimToolkit

julia> data = remd_data(MolSimToolkit.gmx2019_9_log)
```

次に、交換行列をプロットし、交換プロセスの視覚的検査を提供します:

```julia-repl
julia> using Plots

julia> heatmap(data) 
```
