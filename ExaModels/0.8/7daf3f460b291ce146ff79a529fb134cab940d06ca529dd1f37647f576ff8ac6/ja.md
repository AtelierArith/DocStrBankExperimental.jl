```
constraint!(c::C, c1, gen::Base.Generator) where {C<:ExaCore}
```

既存の制約 `c1` を `c` に追加の制約項を指定する `generator` によって拡張します。

# 引数

  * `c::C`: 制約が追加されるモデル。
  * `c1`: 初期の制約値または式。
  * `gen::Base.Generator`: 追加される制約インデックスと項のペアを生成するジェネレーター。

## 例

```jldoctest
julia> using ExaModels

julia> c = ExaCore();

julia> x = variable(c, 10);

julia> c1 = constraint(c, x[i] + x[i+1] for i=1:9; lcon = -1, ucon = (1+i for i=1:9));

julia> constraint!(c, c1, i => sin(x[i+1]) for i=4:6)
制約の拡張

  s.t. (...)
       g♭ ≤ (...) + ∑_{p ∈ P} h(x,p) ≤ g♯

  ここで |P| = 3
```
