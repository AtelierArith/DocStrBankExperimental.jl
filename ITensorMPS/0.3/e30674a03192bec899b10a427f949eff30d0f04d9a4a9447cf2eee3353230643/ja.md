```
truncate!(M::MPS; kwargs...)
truncate!(M::MPO; kwargs...)
```

MPS/MPOのすべてのボンドを切り詰め、キーワード引数として提供された切り詰めパラメータ（cutoff,maxdimなど）を使用します。

キーワード引数:

  * `site_range`=1:N - これらのサイト間のMPSボンドのみを切り詰めます
  * `callback=Returns(nothing)` - ユーザーがボンドごとの切り詰め誤差を保存できるようにするコールバック関数。`callback`のAPIは、`link`と`truncation_error`という2つのキーワード引数を受け取ることを期待しており、`link`は`Pair{Int64, Int64}`型、`truncation_error`は`Float64`型です。以下の例は、1つの可能な使用例を示しています。

```julia
nbonds = 9
truncation_errors = zeros(nbonds)
function callback(; link, truncation_error)
  bond_no = last(link)
  truncation_errors[bond_no] = truncation_error
  return nothing
end
truncate!(ψ; maxdim=5, cutoff=1E-7, callback)
```
