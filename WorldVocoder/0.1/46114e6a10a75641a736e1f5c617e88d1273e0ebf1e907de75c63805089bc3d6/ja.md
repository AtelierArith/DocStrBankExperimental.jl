```
synthesis(f0::Vector{Float64}, spectrogram::Matrix{Float64}, aperiodicity::Matrix{Float64}, fs::Int, frame_period::Float64 = DEFAULT_FRAME_PERIOD)
```

WORLDを使用して、`f0`トラック、スペクトログラム、および非周期性マップからオーディオ信号`y::Vector{Float64}`を合成します。サンプリングレートは1秒あたり`fs`です。オプションで、ミリ秒単位の`frame_period`を指定できます。
