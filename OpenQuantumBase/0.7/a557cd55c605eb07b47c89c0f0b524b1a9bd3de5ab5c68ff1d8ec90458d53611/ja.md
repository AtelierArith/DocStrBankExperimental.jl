```julia
project_to_lowlevel(
    H,
    s_axis,
    coupling,
    dH;
    lvl,
    digits,
    direction,
    refs
)

```

ハミルトニアン `H` を最も低い `lvl` レベルの部分空間に投影します。`s_axis` は、投影が計算される（無次元の）時間のグリッドです。`dH` はハミルトニアンの導関数です。`coupling` はシステム-バス相互作用演算子です。`coupling` と `dH` の両方は、アニーリングパラメータ `s` で呼び出すことができる必要があります。`atol` と `rtol` は、2つの縮退エネルギーレベルを区別するための絶対および相対誤差許容値です。`direction` は `:forward` または `backward` のいずれかで、計算を開始点から始めるか、終点から始めるかを制御します。現在、この関数は縮退エネルギーを持たない実ハミルトニアンのみをサポートしています。
