```
readptx(
    fn::AbstractString, 
    scale::EnergyScale, # ハイパースペクトルのエネルギースケール
    props::Dict{Symbol,Any},
    nch::Int; # ハイパースペクトルのチャンネル数
    blocksize = 1,  # 平均化されたハイパースペクトルを作成するために合計するブロックのサイズ
    dets=[true,true,true,true], # 含める検出器
    frames=1:typemax(Int)) # ハイパースペクトルに含めるフレーム
readptx(
    fn::AbstractString, 
    scale::EnergyScale, # ハイパースペクトルのエネルギースケール
    nch::Int; # ハイパースペクトルのチャンネル数
    blocksize = 1,  # 平均化されたハイパースペクトルを作成するために合計するブロックのサイズ
    dets=[true,true,true,true], # 含める検出器
    frames=1:typemax(Int)) # ハイパースペクトルに含めるフレーム
```

SEMantics .ptxファイルをハイパースペクトルに読み込みます。
