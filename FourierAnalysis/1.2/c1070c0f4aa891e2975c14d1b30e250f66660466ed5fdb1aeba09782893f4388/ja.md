```julia
function taper( kind  :: TaperKind,
                wl    :: Int;
            α       :: Real    = 2.,
            n       :: Int     = ceil(Int, 2*α)-1,
            padding :: Int     = 0,
            type    :: Type{T} = Float64) where T<:Union{Real, Complex}

```

[Taper](@ref)オブジェクトのユニバーサルコンストラクタで、タペリングウィンドウ`kind`（[TaperKind](@ref)型）とウィンドウ長`wl`を指定します。注意：`hamming`および`blackman`タイプの場合は、DSPパッケージとの競合を避けるために`FourierAnalysis.hamming`および`FourierAnalysis.blackman`を使用してください。

すべてのタイプのタペリングに対して長さ`wl`のベクトルを返しますが、dpss（スレピアンマルチターパー）については、サイズ`wl` x `n`の行列を返します。

オプションのキーワード引数`padding`が>0の場合、実際のウィンドウ長は`wl` + `padding`になります。

`type`オプションのキーワード引数は、タペリングウィンドウの要素の型を指定するために使用できます。デフォルトでは、これは`Float64`型です。

オプションのキーワード引数`α`と`n`は、現在スレピアンマルチタピング（*離散プロレート球面系列*）にのみ適用されます：

`α`はDSP.jlパッケージに従った*半帯域幅*（hbw）パラメータです。この単位は多くのdpss実装で使用されており、`α`の「典型的な値」として2、2.5、3、3.5、または4が報告されることがよくあります。しかし、最適なスムージングはウィンドウ長とサンプリングレートの比率に依存して増加するため、これらの値は絶対的な意味では役に立ちません。実際、*hbw*が大きく、`n`が高いほど、スペクトルはより滑らかになります（分散の減少）。これらの問題を克服するために、スレピアンのマルチタピングのために*FourierAnalysis*は[`slepians`](@ref)コンストラクタを実装しており、帯域幅パラメータをHzで指定し、タペリングウィンドウの数を自動的に選択できるようにしています。

`n`はタペリングウィンドウの数です。スレピアンターパーの場合、これは離散プロレート球面系列の数です。DSPパッケージと同様に、デフォルトでは`ceil(Int, 2*α)-1`に設定されていますが、この数が大きい場合、低い固有値は最後の系列に対応する可能性があるため、それらは破棄する必要があります。

**参照**: [タペリングウィンドウのプロット](@ref)。

**関連**: [`slepians`](@ref), [`taperinfo`](@ref)

**例**:

```julia
using FourierAnalysis

## コンストラクタを使用
sr, t, f, a = 128, 128, 10, 0.5
# ホワイトノイズに重ねた正弦波を作成
v=sinusoidal(a, f, sr, t*16, 0) + randn(t*16)
# データ行列を作成
X=broadcast(+, v, randn(t*16, 3))*randn(3, 3)
# ハミングタペリングウィンドウを使用してスペクトルを計算
# `hamming`はDSP.jlでも宣言されているため、'FourierAnalysis.'を前に付ける必要があります
H=taper(FourierAnalysis.hamming, t)
S=spectra(X, sr, t; tapering=H)
# 同じことを取得できます
S=spectra(X, sr, t; tapering=H)
# これはハミングタペリングウィンドウをその場で作成します。
# したがって、同じタペリングウィンドウを何度も再利用する必要がある場合にのみ、
# コンストラクタを明示的に呼び出すことが興味深いです。

## 標準のプロット関数を使用してタペリングウィンドウをプロット
using Plots
tapers=[TaperKind(i) for i=1:8]
X=zeros(t, 8)
for i=1:8 X[:, i] = taper(tapers[i], t).y end
mylabels=Array{String}(undef, 1, 8)
for i=1:8 mylabels[1, i]=string(tapers[i]) end
plot(X; labels=mylabels)

## recipes.jlで宣言されたレシピを使用
plot(taper(parzen, 256))
plot(taper(slepian, 256, α=4, n=7))

```
