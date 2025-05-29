```
CFW(wave::WC, scalingFactor::S=8.0, averagingType::Symbol=:Father,
    boundary::T=WT.DEFAULT_BOUNDARY, averagingLength::Int =
    floor(Int,2*scalingFactor), frameBound::Float64=1.0,
    normalization::Float=Inf) where {WC<:WT.WaveletClass,
    T<:WT.WaveletBoundary, S<:Real}
```

CFW構造体のコンストラクタです。wは連続ウェーブレットのタイプで、scalingFactorはオクターブ$2^J$と$2^{J+1}$の間のウェーブレットの数（デフォルトは8で、音楽や他の音声に最も適しています）。これにより高スケールのウェーブレットが過剰に生成されるため、`decreasing`はオクターブごとにscalingFactorが減少する量を示します。デフォルトの境界条件は`periodic`で、これはベクトルの最後に反転したバージョンを追加することで実装され（エッジの不連続性を排除するため）、代替としては`ZPBoundary`があり、これは最近接の2の累乗に達するために十分なゼロでパディングします（ここで、caveatsによって返される結果が関連します。TorrenceとCompo '97を参照）、`NullBoundary`はデータが本質的に周期的であると仮定します。

`averagingLength`と`averagingType`は、スケール情報がどのように考慮されるかを決定します。`averagingLength`は平均化によってカバーされるウェーブレットオクターブの数を示し、平均化タイプはそれがウィンドウ`Dirac`であるかウェーブレット`Father`であるかを決定します。`frameBound`は全コレクションの総ノルムを示し、上限フレームバウンドに対応します。`normalization`はスケールが変化する際にどのpノルムが保持されるかを指します。`normalization==2`がデフォルトのスケーリングであり、`normalization==Inf`はすべて同じ最大値を与え、ウィンドウのように機能します。
