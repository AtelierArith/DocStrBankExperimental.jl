```
Transmission <: AbstractElement
```

リソースを輸送するために [`Area`](@ref)s の間に使用される [`TransmissionMode`](@ref)s の地理的回廊です。

# フィールド

  * **`from::Area`** はリソースが輸送されるエリアです。
  * **`to::Area`** はリソースが輸送されるエリアです。
  * **`modes::Vector{<:Transmission}`** は利用可能な伝送モードです。
