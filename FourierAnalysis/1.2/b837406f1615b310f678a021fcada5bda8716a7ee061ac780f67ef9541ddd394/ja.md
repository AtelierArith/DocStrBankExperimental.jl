```julia
function filterbank(x         :: Vector{T},
                    sr        :: Int,
                    bandwidth :: IntOrReal    = 2;
                filtkind      :: FilterDesign = Butterworth(2),
                fmin          :: IntOrReal    = bandwidth,
                fmax          :: IntOrReal    = sr÷2,
                ⏩           :: Bool         = true) where T<:Real
```

信号ベクトル `x` をバンドパスフィルタのバンクを通して処理します。サンプリングレート `sr` と `bandwidth` パラメータが与えられます。

フィルタの種類は、DSPパッケージを使用して、オプションのキーワード引数 `filtkind` で指定されます。デフォルトでは、`filtkind` は、各方向において2次の前方-後方（線形位相応答）バターワースIIRフィルタです（したがって、合計4次）。他のIIRおよびFIRフィルタを設計するためのヒントについては、[DSPパッケージの便利な関数に関するノート](@ref)を参照してください。

2つのタプル `(f, Y)` を返します。ここで、`f` はフィルタバンクのバンドパス領域の中心周波数を保持するベクトルであり、`Y` は $i^{th}$ 列に信号 `x` が $i^{th}$ バンドパスフィルタによってバンドパスフィルタ処理されたものを保持する行列です。したがって、`size(Y, 1)=length(x)` であり、`size(Y, 2)=length(f)` です。

フィルタバンクは、引数 `bandwidth` とオプションのキーワード引数 `fmin` および `fmax` によって設計されます。これらの3つの引数は、整数または実数として渡すことができます。すべてのバンドパス領域は、`bandwidth` 引数と等しい帯域幅を持ち、隣接するバンドパス領域と重なります。デフォルトでは、最初のバンドパス領域の下限は `bandwidth` Hz に設定され、次のバンドパス領域はナイキスト周波数 ($sr/2$) まで、ただしそれを除外して定義されます。`fmin` が指定されている場合（Hz単位）、最初のバンドパス領域の中心周波数は `fmin` より下回らないようにできるだけ近くに設定されます。`fmax` が指定されている場合（Hz単位）、最後のバンドパス領域の中心周波数は `fmax` より上回らないようにできるだけ近くに設定されます。

以下は、異なる引数（すべての例で `sr`=16）を用いたフィルタバンク定義のいくつかの例です。

| bandwidth | fmin | fmax |     center frequencies     |                band-pass regions                |
|:---------:|:----:|:----:|:--------------------------:|:-----------------------------------------------:|
|     4     |  -   |  -   |             4              |                       2-6                       |
|     2     |  -   |  -   |       2, 3, 4, 5, 6        |             1-3, 2-4, 3-5, 4-6, 5-7             |
|     2     |  3   |  7   |         3, 4, 5, 6         |               2-4, 3-5, 4-6, 5-7                |
|     1     |  3   |  5   |     3, 3.5, 4, 4.5, 5      |       2.5-3.5, 3-4, 3.5-4.5, 4-5, 4.5-5.5       |
|    1.1    |  3   |  5   | 2.75, 3.3, 3.85, 4.4, 4.95 | 2.2-3.3, 2.75-8.85, 3.3-4.4, 3.85-4.95, 4.4-5.5 |
|    1.9    |  3   |  5   |      2.85, 3.8, 4.75       |           1.9-3.8, 2.85-4.75, 3.8-5.7           |

!!! note "注意"
    出力信号 `Y` の最初と最後には少なくとも `sr` サンプルがトリミングされるべきです。なぜなら、これらのサンプルはフィルタリングプロセスによって著しく歪むからです。

    オプションのキーワード引数 ⏩ が true（デフォルト）である場合、フィルタリングはバンドパスフィルタ間でマルチスレッドで行われます。詳細は [Threads](@ref) を参照してください。


この関数は、時間-周波数表現に対して動作する以下の関数によって呼び出されます：[`TFanalyticsignal`](@ref), [`TFamplitude`](@ref), [`TFphase`](@ref), [`meanAmplitude`](@ref), [`concentration`](@ref), [`meanDirection`](@ref), [`comodulation`](@ref), [`coherence`](@ref)。

**例**:

```julia
using FourierAnalysis, DSP, Plots
# サイン波 + ノイズを生成
f, sr, t = 8, 128, 512
v=sinusoidal(1., f, sr, t, 0)
x=v+randn(t)
flabels, Y=filterbank(x, 128)
flabels, Y=filterbank(x, 128; fmin=4, fmax=32)
flabels, Y=filterbank(x, 128, 4; fmin=4, fmax=32)
flabels, Y=filterbank(x, 128, 4;
                      filtkind=Chebyshev2(8, 10),
                      fmin=4,
                      fmax=16)
# バンドパス領域でフィルタ処理された信号をプロットするためのトリック
for i=1:size(Y, 2) Y[:, i].+=convert(eltype(Y), i)*1.5 end
mylabels=Array{String}(undef, 1, length(flabels))
for i=1:length(flabels) mylabels[1, i]=string(flabels[i])*" Hz" end
plot(Y; c=:grey, labels=mylabels)
```
