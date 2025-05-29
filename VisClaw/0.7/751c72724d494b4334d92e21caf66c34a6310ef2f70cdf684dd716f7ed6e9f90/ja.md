```
plt = plotstrack(track::VisClaw.Track, index::AbstractVector=1:length(track.lon); kwargs...)

plotstrack!(plt::Plots.Plot, track::VisClaw.Track, index::AbstractVector=1:length(track.lon); kwargs...)
```

Plotsを使用して台風/ハリケーントラックをプロットします。
