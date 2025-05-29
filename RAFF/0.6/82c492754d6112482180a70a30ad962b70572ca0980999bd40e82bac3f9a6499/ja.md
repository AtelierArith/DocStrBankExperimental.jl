このタイプはRAFFアルゴリズムの出力ファイルを定義します。

```
RAFFOutput(status::Int, solution::Vector{Float64}, iter::Int,
           p::Int, f::Float64, nf::Int, nj::Int, outliers::Vector{Int})
```

ここで

  * `status`: 収束した場合は1、そうでない場合は0
  * `solution`: モデルのパラメータを持つベクトル
  * `iter`: 収束までの反復回数
  * `p`: 信頼できる点の数
  * `f`: 残差値
  * `nf`: 関数評価の数
  * `nj`: ヤコビアン評価の数
  * `outliers`: 与えられた `p` に対してメソッドによって検出された可能性のある外れ値

    RAFFOutput()

出力のヌルバージョンを作成します。これは `RAFFOutput(0, [], -1, 0, Inf, -1, -1, [])` に相当します。

```
RAFFOuput(p::Int)
RAFFOuput(sol::Vector{Float64}, p::Int)
```

与えられた `p` のための出力のヌルバージョンと、与えられた解を持つヌルバージョンをそれぞれ作成します。
