```
@parameters(def)
```

@stageブロック内で問題のパラメータを定義します。

```julia
@parameters param1, param2, ...
```

デフォルト値を持つ可能性があります。デフォルト値のない定義されたパラメータは、モデルを作成する際に[`instantiate`](@ref)にキーワード引数として供給する必要があります。

## 例

```julia
@parameters d

@parameters begin
    Crops = [:wheat, :corn, :beets]
    Cost = Dict(:wheat=>150, :corn=>230, :beets=>260)
    Budget = 500
end
```

他にも[`@decision`](@ref)、[`@uncertain`](@ref)、[`@stage`](@ref)を参照してください。
