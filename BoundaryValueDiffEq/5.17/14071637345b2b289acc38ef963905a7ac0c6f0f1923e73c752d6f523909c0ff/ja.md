```
BVPSOL(; bvpclass = 2, sol_method = 0, odesolver = nothing)
BVPSOL(bvpclass::Int, sol_methods::Int, odesolver)
```

高度に非線形な**2点境界値問題**を解決するFORTRAN77コードで、局所線形ソルバー（圧縮アルゴリズム）または発生する線形サブ問題の解決のためのグローバルスパース線形ソルバーを使用します。著者はピーター・ドイフラード、ゲオルク・バーダー、ルッツ・ヴァイマンです。詳細なドキュメントについては、[ODEInterface.jl](https://github.com/luchr/ODEInterface.jl/blob/master/doc/SolverOptions.md#bvpsol)を参照してください。

## キーワード引数

```
- `bvpclass`: 境界値問題の分類、デフォルトは悪い初期データを持つ高度に非線形で、利用可能な選択肢：
    - `0`: 線形境界値問題。
    - `1`: 良い初期データを持つ非線形。
    - `2`: 悪い初期データを持つ高度に非線形。
    - `3`: 悪い初期データを持つ高度に非線形で、分離可能な線形境界条件への初期ランク削減。
- `sol_method`: 解法のスイッチ、デフォルトは圧縮アルゴリズムを使用した局所線形ソルバーで、利用可能な選択肢：
    - `0`: 圧縮アルゴリズムを使用した局所線形ソルバーを使用。
    - `1`: グローバルスパース線形ソルバーを使用。
- `odesolver`: `nothing`またはode-solver（dopri5、dop853、seulexなど）。
```

!!! 注     `ODEInterface`パッケージがロードされている場合のみ利用可能です。
