```
remez(numtaps::Integer, band_defs;
      Hz::Real=1.0,
      neg::Bool=false,
      maxiter::Integer=25,
      grid_density::Integer=16)
```

Remez交換アルゴリズムを使用してミニマックス最適フィルタを計算します [^McClellan1973a] [^McClellan1973b]。

これは、2つの必須引数（numtaps、band_defs）だけを受け入れる簡略化されたAPIです。scipy互換のバージョンについては、3つの引数バージョン（numtaps、bands、desired）を参照してください。

Remez交換アルゴリズムを使用して、指定された周波数帯域における望ましいゲインと実現されたゲインの最大誤差を最小化する有限インパルス応答（FIR）フィルタのフィルタ係数を計算します。

# 引数

  * `numtaps::Integer`: フィルタ内の望ましいタップ数。タップ数はフィルタ内の項の数、またはフィルタの次数に1を加えたものです。
  * `bands_defs`: バンド定義のシーケンス。このシーケンスはバンドを定義します。各エントリはペアです。ペアの最初の項はバンドエッジのタプル（低、高）です。ペアの2番目の項は、そのバンド内の望ましい応答と重みを定義します。重みはオプションで、デフォルトは1.0です。望ましい応答と重みの両方はスカラーまたは関数である可能性があります。関数の場合、関数は実数の周波数を受け入れ、実数の望ましい応答または実数の重みを返す必要があります。例：

      * 単位重みのLPF。 `[(0, 0.475) => 1, (0.5, 1.0) => 0]`
      * 停止帯域で重みが2のLPF。 `[(0, 0.475) => (1, 1), (0.5, 1.0) => (0, 2)]`
      * 単位重みのBPF。 `[(0, 0.375) => 0, (0.4, 0.5) => 1, (0.525, 1.0) => 0]`
      * ヒルベルト変換器。 `[(0.1, 0.95) => 1]; neg=true`
      * 微分器。 `[(0.01, 0.99) => (f -> f/2, f -> 1/f)]; neg=true`
  * `Hz::Real`: サンプリング周波数（Hz）。デフォルトは1です。
  * `neg::Bool`: フィルタが負の対称性を持つかどうか。デフォルトはfalseです。falseの場合、フィルタは偶対称です。trueの場合、フィルタは奇対称です。neg=trueは、h[n]=-h[end+1-n]を意味します; neg=falseは、h[n]=h[end+1-n]を意味します。
  * `maxiter::Integer`: （オプション）アルゴリズムの最大反復回数。デフォルトは25です。
  * `grid_density:Integer`: （オプション）グリッド密度。`remez`で使用される密なグリッドのサイズは`(numtaps + 1) * grid_density`です。デフォルトは16です。

# 戻り値

  * `h::Array{Float64,1}`: 最適（ミニマックスの意味で）フィルタの係数を含むランク1の配列。

[^McClellan1973a]: 

J. H. McClellanとT. W. Parks、最適FIR線形位相デジタルフィルタの設計に対する統一アプローチ、IEEE Trans. Circuit Theory, vol. CT-20, pp. 697-701, 1973。

[^McClellan1973b]: 

J. H. McClellan、T. W. ParksおよびL. R. Rabiner、最適FIR線形位相デジタルフィルタを設計するためのコンピュータプログラム、IEEE Trans. Audio Electroacoust., vol. AU-21, pp. 506-525, 1973。

# 例

0.15-0.4 Hzの通過帯域（望ましい応答1）を持つ長さ35のフィルタを構築し、0-0.1 Hzおよび0.45-0.5 Hzの停止帯域（望ましい応答0）を持ちます。注意：これらのバンド間の周波数範囲 - 遷移バンド - の動作は未指定です。

```jldoctest; setup = :(using DSP)
julia> bpass = remez(35, [(0, 0.1)=>0, (0.15, 0.4)=>1, (0.45, 0.5)=>0]);
```

遷移帯域に対して達成される最大誤差をトレードオフできます。遷移バンドが広いほど、指定されたバンド内の最大誤差は低くなります。ここに、同じ通過帯域を持つバンドパスフィルタがありますが、遷移バンドが広くなっています。

```jldoctest; setup = :(using DSP)
julia> bpass2 = remez(35, [(0, 0.08)=>0, (0.15, 0.4)=>1, (0.47, 0.5)=>0]);
```

ここでは、周波数応答を計算し、dBでプロットします。

```julia-repl
julia> using PyPlot
julia> b = DSP.Filters.PolynomialRatio(bpass, [1.0])
julia> b2 = DSP.Filters.PolynomialRatio(bpass2, [1.0])
julia> f = range(0, stop=0.5, length=1000)
julia> plot(f, 20*log10.(abs.(freqresp(b,f,1.0))))
julia> plot(f, 20*log10.(abs.(freqresp(b2,f,1.0))))
julia> grid()
```

# ユニットテストからの例 - 標準（偶）対称性。

長さ151のLPF（ローパスフィルタ）。

```jldoctest; setup = :(using DSP)
julia> h = remez(151, [(0, 0.475) => 1, (0.5, 1.0) => 0]; Hz=2.0);
```

長さ152のLPF。デフォルトでない「重み」入力。

```jldoctest; setup = :(using DSP)
julia> h = remez(152, [(0, 0.475) => (1, 1), (0.5, 1.0) => (0, 2)]; Hz=2.0);
```

長さ51のHPF（ハイパスフィルタ）。

```jldoctest; setup = :(using DSP)
julia> h = remez(51, [(0, 0.75) => 0, (0.8, 1.0) => 1]; Hz=2.0);
```

長さ180のBPF（バンドパスフィルタ）。

```jldoctest; setup = :(using DSP)
julia> h = remez(180, [(0, 0.375) => 0, (0.4, 0.5) => 1, (0.525, 1.0) => 0]; Hz=2.0, maxiter=30);
```

# ユニットテストからの例 - 奇対称フィルタ - ヒルベルトおよび微分器タイプ。

偶数長 - 応答がナイキスト周波数で0に制約されないため、はるかに良い近似を持ちます。長さ20のヒルベルト変換器。

```jldoctest; setup = :(using DSP)
julia> h = remez(20, [(0.1, 0.95) => 1]; neg=true, Hz=2.0);
```

長さ21のヒルベルト変換器。

```jldoctest; setup = :(using DSP)
julia> h = remez(21, [(0.1, 0.95) => 1]; neg=true, Hz=2.0);
```

長さ200の微分器。

```jldoctest; setup = :(using DSP)
julia> h = remez(200, [(0.01, 0.99) => (f -> f/2, f -> 1/f)]; neg=true, Hz=2.0);
```

長さ201の微分器。

```jldoctest; setup = :(using DSP)
julia> h = remez(201, [(0.05, 0.95) => (f -> f/2, f -> 1/f)]; neg=true, Hz=2.0);
```

逆sincフィルタ - カスタム応答関数

```julia-repl
julia> L = 64; Fs = 4800*L;
julia> passband_response_function = f -> (f==0) ? 1.0 : abs.((π*f/4800) ./ sin.(π*f/4800));
julia> h = remez(201, [(    0.0, 2880.0) => (passband_response_function, 1.0),
                (10000.0,   Fs/2) => (0.0, 100.0)]; Hz=Fs);
```
