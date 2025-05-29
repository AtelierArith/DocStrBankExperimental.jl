```
seq = Sequence()
seq = Sequence(GR)
seq = Sequence(GR, RF)
seq = Sequence(GR, RF, ADC)
seq = Sequence(GR, RF, ADC, DUR)
seq = Sequence(GR::Array{Grad,1})
seq = Sequence(GR::Array{Grad,1}, RF::Array{RF,1})
seq = Sequence(GR::Array{Grad,1}, RF::Array{RF,1}, A::ADC, DUR, DEF)
```

Sequence構造体。MRIシーケンスのイベントを含みます。ほとんどのフィールド名（DEFフィールドを除く）は、各列インデックスがシーケンスブロックを表す行列またはベクトルで構成されています。この構造体はシミュレーションの入力として機能します。

# 引数

  * `GR`: (`::Matrix{Grad}`) 勾配行列。行はx-y-z振幅、列はブロックを表します
  * `RF`: (`::Matrix{RF}`) RF行列。1行はコイル用、列はブロック用です
  * `ADC`: (`::Array{ADC,1}`) ADCブロックベクトル
  * `DUR`: (`::Vector`, `[s]`) 持続時間ブロックベクトル
  * `DEF`: (`::Dict{String, Any}`) シーケンスに関連する情報を持つ辞書。可能なキーは[`"AdcRasterTime"`, `"GradientRasterTime"`, `"Name"`, `"Nz"`,   `"Num_Blocks"`, `"Nx"`, `"Ny"`, `"PulseqVersion"`, `"BlockDurationRaster"`,   `"FileName"`, `"RadiofrequencyRasterTime"`]です。

# 戻り値

  * `seq`: (`::Sequence`) Sequence構造体
