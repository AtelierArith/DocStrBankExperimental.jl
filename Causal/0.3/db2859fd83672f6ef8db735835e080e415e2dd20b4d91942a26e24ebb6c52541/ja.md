```julia
mutable struct Link{T}
```

`Link`はデータフローのためにOutpinとInpinを接続します。 [`Outpin`](@ref), [`Inpin`](@ref), [`connect!`](@ref)を参照してください。

# フィールド

  * `buffer::Causal.Buffer{Causal.Cyclic, T, 1} where T`: リンクを通るデータを記録する内部バッファ
  * `channel::Channel`: データフローのための内部チャネル
  * `masterid::Base.UUID`: リンクのソースのOutpinの一意の識別子
  * `slaveid::Base.UUID`: リンクの宛先のInpinの一意の識別子
  * `id::Base.UUID`: 一意の識別子

# 例

```jldoctest
julia> l = Link{Int}(5)
Link(state:open, eltype:Int64, isreadable:false, iswritable:false)

julia> l = Link{Bool}()
Link(state:open, eltype:Bool, isreadable:false, iswritable:false)
```
