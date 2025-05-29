```
PropDict <: AbstractDict{Union{Symbol,Int},Any}
```

PropDictsは、次のことをサポートする辞書です。

コンストラクタ:

```
PropDict(dict::AbstractDict)

PropDict(key1 => value, key2 => value2, ...)
```

構築中に、キーは自動的に`Symbol`と`Int`に変換され、辞書である値は`PropDict`に変換されます。

`PropDict`は深いマージをサポートします:

```julia
x = PropDict(:a => PropDict(:b => 7, :c => 5, :d => 2), :e => "foo")
y = PropDict(:a => PropDict(:c => 42, :d => nothing), :f => "bar")

z = merge(x, y)
@assert z == PropDict(
    :a => PropDict(:b=>7, :d => nothing, :c => 42),
    :e => "foo", :f => "bar"
)

PropDicts.trim_null!(z)
@assert z == PropDict(
    :a => PropDict(:b=>7, :c => 42),
    :e => "foo", :f => "bar"
)
```

存在しないプロパティにアクセスすると、[`PropDicts.MissingProperty`](@ref)のインスタンスが返されます。欠損プロパティの値を設定すると、親の`PropDict`が自動的に作成されます:

```julia
z.foo.bar isa PropDicts.MissingProperty
z.foo.bar = 42
z.foo.bar == 42
```

`PropDict`は、[`readprops`](@ref)および[`writeprops`](@ref)を使用して、JSONファイルに読み書きできます。

!!! note
    `Base.Dict`と同様に、`PropDict`を変更することは*スレッドセーフ*ではありません。

