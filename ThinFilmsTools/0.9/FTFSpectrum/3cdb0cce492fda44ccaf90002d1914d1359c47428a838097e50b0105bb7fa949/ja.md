```
多層スタック内の薄膜のパラメータを、選択したモデルと実験スペクトルを使用して最適化します。

    sol = fit_tmm_optics(
        specType, xinit, beam, Rexp, layers;
        order=1:length(layers), options=Optim.Options(), alg=SAMIN(),
        lb=0.5.*xinit, ub=1.5.*xinit, σ=ones(size(Xexp)), alpha=false,
        oftype=MeanAbs(),
    )

        specType: フィットするスペクトルのタイプで、受け入れられる値は次の通りです：
            Reflectance(Xexp)、Transmittance(Xexp) または Ellipsometry(Xexp)。
            Reflectance() と Transmittance() の場合、フィットするスペクトル配列
            Xexp (0<=Xexp<=1) を渡す必要があります。Ellipsometry() の場合は、
            Ψ (最初の列) と Δ (2番目の列) のスペクトルを度単位で渡す必要があります。
            すなわち、Xexp = [Ψ Δ] です。
        xinit: 最適化のための初期パラメータを含む配列。例えば、システム内の
            2つの層を最適化するには、アルゴリズムのシードを次のようにラップする必要があります：
            xinit = [seed1, seed2]、たとえフィットする層が1つだけであっても、
            xinit = [seed1] とします。各シードの最初のパラメータは常に厚さであり、
            残りは選択したモデルのパラメータです。シードの数は、ModelFit層の数と
            一致する必要があります。
        beam: PlaneWaveからの構造体。
        layers: 層に関する情報を持つ LayerTMMO と ModelFit の列方向配列。
            order: 層の順序を設定します（システムを構築します）。
                このパラメータは、（以前に定義された）layersパラメータに直接結びついています。
                Order は基本的に、layersパラメータ内の各層のインデックスを含みます。
                order の最初と最後のインデックスは、外部媒体であるため、
                ModelFit層に関連付けることはできません。
            options: オプションの Optim.Options 構造体。
            alg: 選択されたオプションのアルゴリズムメソッドで、デフォルトは SAMIN() です。
                例えば、SAMIN(rt=0.1) のようにオプションを渡すこともできます。
                現在、LBFGS()、NelderMead()、および SAMIN() が
                Optim.jl からサポートされています。SAMIN() を選択した場合は、
                lb と ub を入力する必要があります。そうでない場合は、
                xinit 引数の 0.5 倍と 1.5 倍として設定されます。
                LBFGS アルゴリズムは最適化のためにヤコビアンを必要としますが、
                省略可能で、アルゴリズムは数値的に微分を計算します。
            lb: 最適化変数の下限、デフォルトは lb=0.5.*xinit
            ub: 最適化変数の上限、デフォルトは ub=1.5.*xinit
            σ: 各波長のスペクトルの標準偏差を含む配列で、デフォルトは ones(size(Xexp)) です。
            alpha: モデリング層の厚さを線形に減少させるかどうかを手続きに指示します
                (alpha=true) またはしない (alpha=false)。デフォルトは false で、alpha を使用しません。
            oftype: 最適化する目的関数のメトリック。
                値を取ることができます：MeanAbs() (デフォルト)、SumAbs() および SumMeanAbs()。

        sol: 結果を持つ FitTMMOptics 構造体で、フィールドは次の通りです：
            OptimSolverInfo: ソルバーからのステータス情報
            spectrumFit: モデルと最適パラメータで得られたスペクトル
            spectrumExp: 入力実験スペクトル
            optParams: 最適パラメータを含む配列の配列
            objfunMin: 目的関数 MSE の最適値
            beam: 使用された光の構造体
            fitOptions: フィッティング手順の情報を持つ NamedTuple
```
