```
factorize(A::ITensor, Linds::Index...; <keyword arguments>)
```

ITensor `A` を ITensors `L` と `R` に因数分解し、`A ≈ L * R` となるようにします。

# 引数

  * `ortho::String = "left"`: 因数分解の直交性の特性を選択します。

      * `"left"`: 左の因子 `L` は直交基底であり、`L * dag(prime(L, commonind(L,R))) ≈ I` となります。
      * `"right"`: 右の因子 `R` は直交基底を形成します。
      * `"none"`: どちらの因子も直交基底を形成せず、一般的にはできるだけ対称的に作られます（使用される分解に依存します）。
  * `which_decomp::Union{String, Nothing} = nothing`: 使用する分解の種類を選択します。

      * `nothing`: 他の引数に基づいて自動的に分解を選択します。例えば、`nothing` が選択され、`ortho = "left"` または `"right"` が指定され、カットオフが提供されると、提供されたカットオフに応じて `svd` または `eigen` が使用されます（`eigen` はカットオフが `1e-12` より大きい場合にのみ使用されます。精度が低いためです）。切り捨てが要求されない場合、密な ITensors には `qr` が使用され、ブロックスパース ITensors には `svd` が使用されます（将来的にはこの場合、ブロックスパース ITensors にも `qr` が使用される予定です）。
      * `"svd"`: `L = U` および `R = S * V` は `ortho = "left"` の場合、`L = U * S` および `R = V` は `ortho = "right"` の場合、`L = U * sqrt.(S)` および `R = sqrt.(S) * V` は `ortho = "none"` の場合です。どの `svd` アルゴリズムを選択するかを制御するには、`svd_alg` キーワード引数を使用します。サポートされているアルゴリズムについては `svd` のドキュメントを参照してください。これらは `alg` キーワード引数で受け入れられるものと同じです。
      * `"eigen"`: `L = U` および $R = U^{\dagger} A$ で、`U` は固有分解 $A A^{\dagger} = U D U^{\dagger}$ から決定されます。`ortho = "left"` の場合（`ortho = "right"` の場合はその逆）。`"eigen"` は `ortho = "none"` ではサポートされていません。
      * `"qr"`: `L=Q` および `R` は上三角行列で、`ortho = "left"` の場合、`R = Q` および `L` は下三角行列で、`ortho = "right"` の場合（現在は密な ITensors のみサポートされています）。将来的には、QR（ブロックスパース ITensors 用）、極、コレスキー、LU などの他の分解もサポートされる予定です。

切り捨て引数については、次を参照してください: [`svd`](@ref)
