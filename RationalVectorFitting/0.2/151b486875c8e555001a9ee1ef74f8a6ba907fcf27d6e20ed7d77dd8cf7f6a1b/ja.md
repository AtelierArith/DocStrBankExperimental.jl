```
vector_fitting(
    s,
    f,
    init_poles,
    weight = 1;
    relaxed = true,
    force_stable = true,
    maxiter = 5,
    tol = 1e-12,
) -> poles, residues, d, h, fitted, error_norm
```

複素周波数 `s` を持つ配列 `f` のベクトルフィッティングを初期極 `init_poles` のセットを使用して行います。

`f` は次元 `(Ns, Nc)` の行列であり、フィッティングはその列に対して共通の極のセットを使用して行われます。

`relaxed` は非自明性制約を制御します。`relaxed=true` は通常、収束が速くなりますが、滑らかでない関数に対しては安定性が低下する可能性があります。

`force_stable` は不安定な極が半左複素平面に反映されるべきかどうかを制御し、すなわち負の実部を持つように強制されます。

`maxiter` は、所望の `error_norm` 許容誤差 `tol` で収束を達成しようとするために行われる最大反復回数です。

他にも [`recommended_init_poles`](@ref)、[`rational`](@ref)、[`pole_identification`](@ref)、[`residue_identification`](@ref) を参照してください。
