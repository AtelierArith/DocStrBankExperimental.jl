```julia
   (1)
   function analyticsignal( X  :: Union{Vector{T}, Matrix{T}},
                            wl :: Int     = size(X, 1);
                        nonlinear :: Bool    =  false,
                        planner   :: Planner =  getplanner,
                        ⏩       :: Bool    =  true) where T<:Real

   (2)
   function analyticsignal( 𝐗      :: Vector{Matrix{T}},
                            wl     :: Int;
                        nonlinear  ::  Bool      =  false,
                        planner    ::  Planner   =  getplanner,
                        ⏩        ::  Bool      =  true) where T<:Real
```

(1)

ベクトル `X` または行列 `X` のすべての列ベクトルの解析信号（AS）をFFTおよびiFFT手法を介して計算します。これはMarple（1999）で説明されています。 `wl`=size(X, 1)（デフォルト）の場合、`X`内のすべてのサンプルを一緒にFFTおよびiFFTに渡す標準的な方法を使用しますが、`wl`<size(X, 1)の場合はスライディングウィンドウ法が使用されます（以下を参照）。

解析信号 `𝑌` を返します。`X` がベクトルの場合は複素ベクトル、`X` が行列の場合は `X` の列の解析信号を保持する複素行列です。`𝑌` は `X` と同じ数のサンプル（行）を持ちます。

[DSP](https://github.com/JuliaDSP/DSP.jl) パッケージで行われていることとは異なり、信号のDCレベルは除去されます。したがって、入力信号にゼロでないDCレベルが含まれている場合、ASの実部はDCレベルが除去された入力信号と等しくなります。`𝑌` の虚部は、そのようなDCなしの `X` のヒルベルト変換です。

スライディングウィンドウASは、ベクトルおよび行列が非常に大きい場合にASの効率的な推定を可能にします。これは、50％のスライディングオーバーラップウィンドウでASを計算し、各ウィンドウの中央の半分を保持することによってASを形成します。最終的な推定を得るために実際に使用されるポイントの数は $wl$÷2（整数除算）です。推定を使用するには、`wl` は偶数でなければなりません。この手法はエッジ効果を生じさせるため、AS推定の最初と最後の $wl÷4$ サンプルは破棄する必要があります。実際には、より大きなデータセグメントのASが必要であり、推定の開始と終了で少なくとも $wl÷4$ サンプルをトリムします。これは自動的に [`TFanalyticsignal`](@ref) 関数によって行われます。

また、スライディングウィンドウAS法は、サンプル $wl$÷4 およびその後の $wl$÷2 サンプルごとに小さな不連続性を生じさせるため、`wl` はできるだけ大きく選択する必要があります。

!!! note "Nota Bene"
    非常に長いエポックのFFT計算を避けるために、`wl` > 2^14 の場合、`wl` は 2^10 に設定されます。この制限を下回る場合、計算が実行可能である限り、標準的な方法を使用します。スライディングウィンドウ法を絶対に使用する必要がある場合は、効率的に引数 `wl` を設定するために [window length in FFTW](@ref) を参照してください。

    入力信号は、`wl` サンプルのウィンドウで得られる最初の離散フーリエ周波数よりも低い周波数成分を含まないように、事前にバンドパスまたはハイパスフィルタリングされるべきです。つまり、sr/wl Hz よりも低い周波数成分を含まないようにする必要があります。ここで、sr はサンプリングレートです。


**オプションのキーワード引数**:

`nonlinear` が true の場合、解析信号はその振幅がすべてのポイントで $1.0$ になるように正規化されます。これにより、非線形の単変量および二変量推定が可能になります（[timefrequencyuni.jl](@ref) および [timefrequencybi.jl](@ref) を参照）。

`planner` は、FFTおよびiFFTを計算するために使用される前方および後方FFTWプランを保持する [`Planner`](@ref) オブジェクトのインスタンスです。デフォルトではプランナーが計算されますが、事前に計算された場合はここで引数として渡すことができます。これは、`analyticsignal` 関数が繰り返し呼び出される場合に興味深いです。

`⏩` が true の場合、`X` 内の系列の数がJuliaに指示されたスレッドの数の少なくとも2倍である場合、メソッドはマルチスレッドモードで実行されます。[Threads](@ref) を参照してください。

(2)

ベクトルの行列 `𝐗` として与えられたすべての $k$ 多変量データ行列の解析信号を計算します。メソッド（1）と同様に、対応する解析信号を保持する行列のベクトルを返します。FFTおよびiFFTプランは一度だけ計算されます。`𝐗` 内の $k$ 行列は、異なる列数（すなわち、異なる系列数）および異なる行数（サンプル数）を持つ場合があります。ただし、すべての行列の行数は `wl` より大きくなければなりません。

`⏩` が true の場合、このメソッドは `𝐗` 内の行列に対してマルチスレッドモードで実行されます。行列の数がJuliaに指示されたスレッドの数の少なくとも2倍でない場合、メソッド（1）に従って各解析信号推定をマルチスレッドモードで実行しようとします。[Threads](@ref) を参照してください。

この関数は、時間-周波数表現に対して動作する次の関数によって呼び出されます：[`TFanalyticsignal`](@ref)、[`TFamplitude`](@ref)、[`TFphase`](@ref)、[`meanAmplitude`](@ref)、[`concentration`](@ref)、[`meanDirection`](@ref)、[`comodulation`](@ref)、[`coherence`](@ref)。

**参考文献** Marple S.L. (1999) FFTを介して離散時間解析信号を計算する。IEEE Transactions on Signal Processing 47(9), 2600-3。

**例**:

```julia
using FourierAnalysis, FFTW, LinearAlgebra, Statistics, Plots, DSP
t=128; lab=["x", "real(y)", "imag(y)"]

# 1つのベクトルの解析信号
x=sinusoidal(10, 2, 128, t, π/2; DC=10) # コサイン
y=analyticsignal(x)
# note that real(y) is x without the DC level, i.e., x=real(y)+DC
plot([x, real(y), imag(y)]; labels=lab)

# チェックを行う
s=sinusoidal(10, 2, 128, t, 0) # サイン
norm(s-imag(y)) # should be zero

# DSP.jlによる解析信号
y2=hilbert(x)
norm(s-imag(y2)) # should be zero
# DSP.jlはDCレベルを除去しない
# したがって、この場合 x=real(y2)
plot([x, real(y2), imag(y2)]; labels=lab)

# 複数のベクトルの解析信号
x=hcat(x, sinusoidal(10, 3, 128, t, π/2; DC=10))
y=analyticsignal(x)

# 1つのベクトルのスライディングウィンドウ解析信号
# （エッジ効果に注意）
x=sinusoidal(10, 2, 128, t*4, π/2; DC=0)
y=analyticsignal(x, t)
plot([x, real(y), imag(y)]; labels=lab)

# 複数のベクトルのスライディングウィンドウ解析信号
x=hcat(x, sinusoidal(10, 3, 128, t*4, π/2; DC=0))
y=analyticsignal(x, t)
```
