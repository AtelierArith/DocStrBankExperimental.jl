```
propagator(size::NTuple{N, Int}; Δz=1.0, shift_by=(0,0), k_max=0.5, offset=CtrFT, scale=ScaFT, dims=ntuple(+, N), accumulator=sum, weight=1) where {N,T}

自由空間伝播における位相変化を記述する複素値位相であり、`k_z= Δz * sqrt(1-k_x^2-k_y^2)` です。

引数 `shift_by` と `Δz` はリストモードをサポートしており、これを使用することで複数のシフトを同時に便利に実行できます。

# 引数:
* `offset`: ガウスの中心位置。タプルまたはインジケーター `CtrCorner`, `CtrEnd`, `CtrFT`, `CtrRFT` などを使用できます。
* `Δz`: 実空間の第三次元 z に沿って伝播する量で、媒質内の波長の単位（すなわち倍数）で表されます（`λ = n*λ₀`）。  
* `shift_by`: 実空間の x および y 空間方向にシフトする量。
* `k_max`: ナイキスト周波数に対するサンプリングを示します。光学では、`pixelpitch./λ` であり、`pixelpitch` はタプルで、媒質内の波長 `λ = n*λ₀` です。
* `scale`: ピクセルのスケール。デフォルトでは `ScaUnit` が仮定されます。
* `dims`: この関数を適用する次元。
* `weight`: 結果の強度。リストモードをサポートします（ドキュメントは rr2 を参照）。
* `accumulator`: リストモードデータを重ね合わせるために使用される方法。リストモードでのみ適用されます。
```

## 参照: `phase_kz()`

屈折率 1.0 および真空波長 `λ` 500nm の 2D プロパゲーターの例で、すべての三次元空間で 250 nm の `sampling` を持ちます。最後の行は、異なる z 平面ごとに均一な z に沿った `sampling` が `sampling[3]` である 2D プロパゲーターのスタックを取得する方法を示しています。`propagator()` は波長や屈折率について知る必要はなく、その入力は波長の倍数として指定されます。また、この例は結果の振幅に対してナイキストサンプリングをほぼ満たしますが、強度は 2 倍のファクターでアンダーサンプリングされることに注意してください。`propagator` では完全な数値開口 (NA) が仮定されており、ユーザーは可能な NA 制限に注意する必要があります。詳細については `PointSpreadFunctions.jl` パッケージを参照してください。

```jldoctest
julia> using IndexFunArrays

julia> sz = (150,100,100); n=1.0; λ=0.500; sampling=(0.250, 0.250, 0.250);     

julia> prop = propagator(sz[1:2]; Δz=sampling[3]/(λ/n), k_max=sampling[1:2]./(λ/n));

julia> prop3d = prop.^zz((1,1,sz[3])); # スタックのためのプロパゲーターの系列
```

---

propagator(arr::AbstractArray; Δz=1.0, shift*by=(0,0), k*max=0.5, offset=CtrFt, scaling=ScaUnit)

これは `propagator(eltype(arr), size(arr), Δz=Δz, shift_by=shift_by, k_max=k_max, scaling=scaling, offset=offset)` のラッパーです。
