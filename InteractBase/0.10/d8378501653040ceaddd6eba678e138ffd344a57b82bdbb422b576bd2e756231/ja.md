```
function rangepicker(vals::AbstractArray;
                value=[extrema(vals)...],
                label=nothing, readout=true, kwargs...)
```

ハンドルごとに1つのスピンボックスを持つマルチハンドルスライダー。
