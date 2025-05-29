```
synth(cfg::SHTnsCfg, qlm)
synth(cfg::SHTnsCfg, slm, tlm)
synth(cfg::SHTnsCfg, qlm, slm, tlm)
```

Transforms spherical harmonics coefficients `qlm` into spatial data `v`; `slm` and `tlm` into spatial data `utheta` and `uphi`; `qlm`, `slm` and `tlm` into spatial data `ur`, `utheta` and `uphi`.
