```
bubblebath!(
    spheres::Vector{Sphere{D}},
    radius_pdf, ϕ_max::Real, extent::NTuple{D,Real};
    min_distance::Real = 0.0, through_boundaries = false,
    max_tries = 10000, max_fails = 100,
    verbose = true, rng = default_rng()
) where D
```

`bubblebath`のインプレースバージョンで、すでに populated されている可能性のある `spheres` ベクターに新しい球体を追加します。

ここで、`ϕ_max` は `spheres` ベクターにすでに存在する球体を考慮していません。例えば、`packing_fraction(spheres, extent)` が 0.2 で `ϕ_max=0.3` の場合、アルゴリズムは 0.3 のパッキング分率のために新しい球体を生成し、挿入時には合計で 0.5 のパッキング分率を（試みて）追加します。事前に初期化された球体を考慮するために、`ϕ_max` を適切に減少させます（この例では `ϕ_max = 0.3-packing_fraction(spheres,extent)` で 0.1 になります）。
