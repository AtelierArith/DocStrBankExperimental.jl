FFTWプランは、**フーリエ解析**内のすべての関数で使用されるため、この構造体にカプセル化されています。これはこのパッケージによって作成される唯一の*オペレーターオブジェクト*であり、他はすべて*データオブジェクト*です。

スペクトルおよびクロススペクトル計算（周波数領域オブジェクト）は、前方プラン（実FFT）のみを必要とし、解析信号に基づくオブジェクト（時間-周波数領域オブジェクト）は、前方（`.p`）および後方（`.ip`）プラン（複素iFFT）の両方を必要とします。

引数`flags`は、上記の定数のいずれかでなければなりません。フラグの基本的な使用法は、プランナーを計算するのに必要な時間とFFTを計算するための効率との間のトレードオフを含みます。以下のフラグは、計算に必要な時間と効率の昇順に並べられています：`plan_estimate`、`plan_measure`、`plan_patient`、`plan_exhaustive`。デフォルトでは*FourierAnalysis*は`plan_estimate`を採用しており、最も迅速な検索を可能にしますが、最適な選択ではありません。他のフラグは、同じ設定で複数のFFT計算を行う場合に価値があるかもしれません。詳細については[こちら](http://www.fftw.org/fftw3_doc/Planner-Flags.html)を参照してください。

引数`timelimit`は、FFTWがプランを最適化するために許可される最大時間（秒単位）です。これを`-1.0`に設定すると、時間制限が課されないことになります。

FFTWプランは、指定されたウィンドウ長`wl`とデータ型`type`に対して計算されます。

`Planners`オブジェクトは、以下の`Planner`コンストラクタのいずれかを使用して、[FDobjects](@ref)および[TFobjects](@ref)のコンストラクタに引数として渡すことができます。

**コンストラクタ**

```julia
Planner(flags :: UInt32,
    timelimit :: Union{Int, Float64},
           wl :: Int,
         type :: Type,
           bw :: Bool = false)
```

これを使用して、FFTの`flags`定数と`timelimit`、ウィンドウ長`wl`、および入力データの型`type`（実数である必要があります、例：Float64）を引数として渡してPlannerオブジェクトを作成します。

`bw`がfalse（デフォルト）の場合、ダミーの後方プランが作成されます。そうでない場合、`type`に対応する複素データ型の後方プランが作成されます（例：`type`がFloat64の場合、ComplexF64データ用に作成されます）。

例えば、𝐗が1秒あたり128サンプルでサンプリングされた多変量時系列の多くの行列のベクトルであり、256ポイントFFTを使用してすべてのスペクトルを計算したいとします。最初に次のようにプランを作成します。

```julia
p=Planner(plan_exhaustive, 10.0, 256, eltype(𝐗[1]))
```

次に、プランを引数として渡して[Spectra](@ref)関数を呼び出します：

```julia
𝐒=spectra(𝐗, sr, t; planner=p)
```

データの型がFloat64であり、前方プランのみが必要な場合は、短い構文が利用可能です：

```julia
Planner(flags :: UInt32,
    timelimit :: Union{Int, Float64},
           wl :: Int)
```

例えば、上記の行は次のように短く書くことができました。

```julia
p=Planner(plan_exhaustive, 10.0, 256)
```

後方プランも作成するには、代わりに次のように使用します。

```julia
p=Planner(plan_exhaustive, 10.0, 256, eltype(𝐗[1]), true)
```
