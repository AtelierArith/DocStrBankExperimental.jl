```
struct ConsecutiveParamArray{T,N,M,A<:AbstractArray{T,M}} <: ParamArray{T,N}
  data::A
end
```

メモリに連続して格納されたエントリを持つパラメトリック配列です。これは、`size(data)[1:N]` に等しい内部サイズと、`size(data,N+1)` に等しいパラメトリック長を持つことが特徴です。ここで、`data` は次元 `M = N+1` の `AbstractArray` です。
