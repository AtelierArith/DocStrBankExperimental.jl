```
Protocol(
bval::Vector{Float64}
techo::Vector{Float64}
tdelta::Vector{Float64}
tsmalldel::Vector{Float64}
gvec::Vector{Float64}
bvec::Matrix{Float64}
nmeas::Vector{Float64}
)
```

取得プロトコルに関連するパラメータを保持するためのプロトコルタイプオブジェクトを返します。これにはb値、tcho時間、拡散勾配の分離、持続時間、強度、方向、および測定の数が含まれます。単位の慣習：ほとんどのテキストファイルではb値にs/mm^2、時間にmsを使用しますが、これらはプロトコル内でSI単位に変換されます。b値（s/m^2）；時間（s）；サイズ（m）；G（T/m）

```
Protocol(
    filename::String
)
```

球面平均関数から生成されたbテーブルファイルからプロトコルタイプオブジェクトを返します。

```
Protocol(
    bval::Vector{Float64},
    techo::Vector{Float64},
    tdelta::Vector{Float64},
    tsmalldel::Vector{Float64},
)
```

`gvec`を計算し、提供されたパラメータからプロトコルタイプオブジェクトを返します。他のフィールドは役に立ちません。

```
Protocol(
    dmri::dMRI
)
```

dMRIオブジェクトからプロトコルタイプオブジェクトを返します。
