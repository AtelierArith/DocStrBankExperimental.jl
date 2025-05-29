```
omega(x)
ω(x)
```

与えられたベクトルの最後のインデックスを返します。死亡率ベクトルの場合、これは定義された率の最後に達した年齢を意味します。

`omega`は選択テーブルの発行年齢によって異なる場合があり、選択された`omega`はテーブルの最終的な`omega`と異なる場合があります。

ωはomegaのエイリアスですが、エクスポートされていません。使用するには、インポート時に`using MortalityTables: ω`を実行するか、`MortalityTables.ω()`を呼び出してください。

# 例

```julia-repl
julia> qs = UltimateMortality([0.1,0.3,0.6,1]);
julia> omega(qs)
3

julia> qs = UltimateMortality([0.1,0.3,0.6,1],start_age=10);
julia> omega(qs)
13

```
