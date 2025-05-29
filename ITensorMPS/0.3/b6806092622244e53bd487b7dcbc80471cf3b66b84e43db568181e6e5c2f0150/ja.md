```
projector(x::MPS; <keyword argument>) -> MPO
```

状態 `x` への射影演算子を計算します。ディラック記法では、これは演算 `|x⟩⟨x|/|⟨x|x⟩|²` です。

キーワード引数を使用して切り捨てのレベルを制御します。これらは `contract(::MPO, ::MPO; kw...)` によって受け入れられるものと同じです。

# キーワード

  * `normalize::Bool=true`: 射影演算子を形成する前に入力 MPS を正規化するかどうか。`normalize==false` で、入力 MPS がすでに正規化されていない場合、この関数は適切な射影を出力せず、単に `outer(x, x) = |x⟩⟨x|` を出力します。つまり、射影演算子は `norm(x)^2` でスケーリングされます。
  * 切り捨てキーワード引数は `contract(::MPO, ::MPO; kw...)` によって受け入れられます。

[`outer`](@ref) や [`contract`](@ref) も参照してください。
