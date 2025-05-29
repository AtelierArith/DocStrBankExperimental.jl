```
cut2sph(cut::Cut; keywords...) -> sph::SPHQPartition

cut2sph(cuts::AbstractVector{Cut}; keywords...) -> sphs::Vector{SPHQPartition}

cut2sph(cutfile::AbstractString; kwargs...) -> s::SPHQPartition
```

`Cut`オブジェクトをHansen 1988年の書籍「Spherical Near-Field Antenna Measurements」の再帰的FFT/IFFTメソッドを使用して`SPHQPartition`に変換します。

単一の位置引数は、Ticra互換の球面極切断ファイルの名前を含む文字列、またはそのようなファイルを`read_cutfile`で読み込むことによって得られる`Cut`型の値（または`Cut`オブジェクトのベクター）である可能性があります。この関数の出力は、Ticra互換のQ型球面波係数ファイルを作成するために`write_sphfile`に渡すことができます。入力されたカットが3つの偏光スロットを含む場合、変換を行う前に3番目のスロットは破棄されます。

入力されたカットがθのみにθ₀ < 180°まで拡張されている場合、θ₀ < θ ≤ 180°の範囲ではフィールドが同一にゼロであると仮定されます。

## キーワード引数（およびそのデフォルト値）

  * `mmax=1000`: 含める`m`（方位）モードインデックスの上限。実際の上限は、奇数の`Nϕ`の場合は`min(Nϕ÷2, mmax)`、偶数の`Nϕ`の場合は`min(Nϕ÷2-1, mmax)`に設定されます。ここで、`Nϕ`はカットオブジェクト内のϕ = 定数極切断の数です。
  * `nmax=1000`: 含める`n`（極）モードインデックスの上限。実際の上限は、`nmax`と`Nθ-1`のうち小さい方であり、ここで`Nθ`は各ϕ = 定数極切断に含まれるθ値の数です。
  * `pwrtol=0.0`: パワートレランス。除外されたモードのパワーが総モーダルパワーの`pwrtol`倍未満になるまで球面モードが含まれます。ゼロまたは負の値は、モードの削除を妨げます。
