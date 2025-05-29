```
realization(p::ParamSpace;nparams=1,sampling=get_sampling_style(p),kwargs...) -> Realization
realization(p::TransientParamSpace;nparams=1,sampling=get_sampling_style(p),kwargs...) -> TransientRealization
```

与えられたパラメトリック空間から `nparams` パラメータのセットを抽出します。デフォルトでは、`p` に指定されたサンプリング戦略に従います。
