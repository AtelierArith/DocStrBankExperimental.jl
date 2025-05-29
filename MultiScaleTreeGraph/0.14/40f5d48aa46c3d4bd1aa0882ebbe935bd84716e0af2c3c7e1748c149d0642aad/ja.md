```
select!(node::Node, args..., <keyword arguments>)
select(node::Node, args..., <keyword arguments>)
```

`args...`で選択されていないすべての属性を削除し、選択された変数に対してオプションで変換を適用します。この関数は[`transform!`](@ref)と似たように動作しますが、選択された変数のみを保持し、[`transform!`](@ref)は新しい変数を追加します。

`args`の形式や引数の使い方についての詳細は、[`transform!`](@ref)のドキュメントを参照してください。

この関数は`args...`にもう1つの形式を追加します：変数名を指定して変数を選択するだけです。

# 例

```julia
file = joinpath(dirname(dirname(pathof(MultiScaleTreeGraph))),"test","files","simple_plant.mtg")
mtg = read_mtg(file)

select!(mtg, :Length => (x -> x / 10) => :length_m, :Width, ignore_nothing = true)
```
