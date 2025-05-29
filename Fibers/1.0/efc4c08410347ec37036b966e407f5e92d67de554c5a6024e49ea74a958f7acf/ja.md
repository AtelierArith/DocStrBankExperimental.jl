```
Base.show(mri::MRI; plane::Char='a', z::Union{Int64, Nothing}=nothing, t::Union{Int64, Nothing}=nothing, title::Union{String, Nothing}=nothing)
```

指定された`plane`（'a': 軸方向; 's': 矢状面; 'c': 冠状面）に沿って、`MRI`構造体の`t`-番目のフレームから`z`-番目のスライスを表示します。
