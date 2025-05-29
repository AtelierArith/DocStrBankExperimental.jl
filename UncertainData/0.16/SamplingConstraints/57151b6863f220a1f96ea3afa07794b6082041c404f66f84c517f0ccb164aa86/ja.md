```
constrain(uv::AbstractUncertainScalarKDE,
    constraint::SamplingConstraint) -> TruncatedUncertainScalarKDE
```

`constraint`を適用し、カーネル密度推定によって表される不確実な値`uv`のサポートを切り詰めます。
