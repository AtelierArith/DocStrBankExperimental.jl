```julia
CLAMP(
    s,
    k,
    skop,
    σX;
    nb_inits,
    tuning,
    tuning_max_its,
    SHyGAMP_max_its,
    sketch_tol,
    uniform_integration_nrep,
    uniform_vars,
    check_finite,
    clip_bad_Qs,
    τ_init,
    debug,
    debug_dic
)

```

「圧縮学習近似メッセージパッシング」アルゴリズム。スケッチ `s` から `k` セントロイドを復元します。
