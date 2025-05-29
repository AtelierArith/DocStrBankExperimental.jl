```julia
struct VortexFilament{TV<:(AbstractVector{<:AbstractVector}), TI<:AbstractVector{Int64}}
```

強さ `Γ` の渦フィラメントを定義し、`vertices` における頂点と、頂点を接続する `segments` によって離散化されます。`segments` の各セグメントは、`vertices` の2つの連続したエントリを接続する必要があります。頂点は、そのインデックスが `boundidx` に現れる場合、境界としてマークされることがあります（例：翼に対して）。同様に、渦は、そのインデックスが `freeidx` に現れる場合、自由な頂点としてマークされます。

# フィールド

  * `Γ`: Γ: 渦フィラメントの強さ。
  * `vertices`: vertices: 渦フィラメントの頂点の配列。
  * `segments`: segments: 渦フィラメントのセグメントの配列。
  * `freeidx`: freeidx: 渦フィラメントの自由な頂点のインデックスの配列。
  * `boundidx`: boundidx: 渦フィラメントの境界の頂点のインデックスの配列。

```
