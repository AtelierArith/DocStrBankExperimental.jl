```
Hartmut <: AbstractHeadmodel
```

HArtMuTモデル（Harmening et al., 2022）にアクセスするための型で、脳のソースだけでなく、筋肉および眼のソースも含む頭部モデルです。

注意: この頭部モデルのインスタンスを作成するには `Hartmut()` を使用してください。

# フィールド

  * `artefacual::Any`: ラベル、リードフィールド、方向、位置を含む、筋肉および眼のようなアーティファクトソースの辞書。
  * `cortical::Any`: ラベル、リードフィールド、方向、位置を含む皮質ソースの辞書。
  * `electrodes::Any`: 電極のラベルと3D空間での位置を含む辞書。

# 例

```julia-repl
julia> h = Hartmut()
Please cite: HArtMuT: Harmening Nils, Klug Marius, Gramann Klaus and Miklody Daniel - 10.1088/1741-2552/aca8ce
HArtMuT-Headmodel
227 electrodes:  (AF3,AF3h...) - hartmut.electrodes
2004 source points: (Left Middle Temporal Gyrus, posterior division,...) - hartmut.cortical
4260 source points: (Muscle_DepressorLabii_left,...) - hartmut.artefactual

In addition to UnfoldSim.jl please cite:
HArtMuT: Harmening Nils, Klug Marius, Gramann Klaus and Miklody Daniel - 10.1088/1741-2552/aca8ce

# アーティファクトソースにアクセス
julia> h.artefactual
Dict{String, Any} with 4 entries:
  "label"       => ["Muscle_DepressorLabii_left", "Muscle_DepressorLabii_left", "Muscle_DepressorLabii_left", "Muscle_DepressorLabii_left", "Muscle_DepressorLabii_left", "Muscle_DepressorLabii_left", "Muscle_DepressorLabii_left", "Mu…
  "leadfield"   => [-0.00148682 -0.00229078 … -0.307231 -0.321305; 0.0141537 0.0134523 … -0.141177 -0.140583; … ; 0.108747 0.1091 … 0.106614 0.117126; 0.0257134 0.0248186 … 0.00105064 -0.00433068;;; 0.0898798 0.0891799 … 2.02466 1.81…
  "orientation" => [0.54244 0.482395 -0.687789; 0.546949 0.507161 -0.666059; … ; 0.193693 -0.979684 0.0519768; 0.327641 -0.944196 -0.0338583]
  "pos"         => [-29.3728 58.6061 -120.829; -28.4183 59.0185 -121.448; … ; -21.8088 70.5968 -28.7679; -21.1545 70.1282 -31.4184]
```
