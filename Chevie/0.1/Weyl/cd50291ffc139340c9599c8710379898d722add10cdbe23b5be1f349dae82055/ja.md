`rootdatum(R::AbstractMatrix,CR::AbstractMatrix)`

は、`R` の行である単純根と、`CR` の行である単純コルートによって与えられるルートデータを構築します。これは、`R` の行空間上の反射群であり、反射 `reflectionMatrix(R[i,:],CR[i,:])` によって生成されます。

別の解釈では、これは代数群のルートデータを構築します。ここで、`R` の行は基底 `X(T)` 上の単純根であり、`CR` の行は基底 `Y(T)` 上の単純コルートです。この解釈において、以下のメソッドはすべて `gl₃` を定義します。

```julia-repl
julia> rootdatum(:gl,3)==rootdatum("gl",3)
true

julia> rootdatum([1 -1 0;0 1 -1],[1 -1 0;0 1 -1])
A₂Φ₁
```
