```
groupparams(m::AbstractModel, cols::Symbol...)
```

`m`のパラメータを`cols`に従って階層的にグループ化します。各パラメータフィールドの値型に対して`Symbol`コンストラクタが定義されている必要があります（例えば、`String`、`Symbol`、および`Int`はデフォルトで有効です）。返される値は、階層的な順序が`cols`の順序に従ったネストされた名前付きタプルです。

例えば、最初にコンポーネント名で、次にフィールド名でパラメータをグループ化することができます：

# 例

```julia-repl
julia> groupparams(Model((a=Param(1.0), b=Param(2.0))), :component, :fieldname)
(NamedTuple = (a = ..., b = ...),)
```
