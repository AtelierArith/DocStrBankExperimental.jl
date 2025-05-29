```
getchemicalattr(chemical::Chemical, ::Val{T}; kwargs...)
getchemicalattr(chemical::Chemical, ::Val{:name}; kwargs...)
getchemicalattr(chemical::Chemical, ::Val{:formula}; kwargs...) 
getchemicalattr(chemical::Chemical, ::Val{:elements}; kwargs...)
getchemicalattr(cc::Chemical, ::Val{:charge}; kwargs...)
getchemicalattr(chemical::Chemical, ::Val{:abundant_chemical}; kwargs...)
```

`chemical`から属性（`attr`）を取得します。`:name`および`:formula`以外の属性については、`chemical.attr`を反復処理します。一致する属性名が見つからない場合は、`nothing`を返します。
