```
光学厚さと多孔性の2つのパラメータのウィンドウ範囲に対する解空間を計算します。これら2つのパラメータと、入射媒体と出現媒体の間の単一層に対してのみ機能します。

    sol = space_solution_ema(specType, b, beam, Xexp, layers; oftype=MeanAbs())

        specType: フィットさせるスペクトルのタイプで、受け入れられる値は次のとおりです：
            Reflectance(Xexp)、Transmittance(Xexp)、または Ellipsometry(Xexp)。
            Reflectance() と Transmittance() の場合、フィットさせるスペクトル配列
            Xexp（0から1の間）を渡す必要があります。Ellipsometry() の場合は、
            Ψ（最初の列）と Δ（2番目の列）のスペクトルを度単位で渡す必要があります。
        b: 光学厚さと多孔性の下限と上限。
           （例：[odl, odu, pl pu; Nod, Np]）、ここで Nod と Np は解空間内で
           探索するポイントの数を示すオプションのパラメータです。
        beam: PlaneWave からの構造
        layers: 層に関する情報を持つ3つの LayerTMMO と ModelFit の列方向配列。
            space_solution_ema の場合：length(vec(layers)) = 3。最初と3番目の層の
            タイプは LayerTMMO であり、2番目の層のタイプは ModelFit です。
            oftype: 最適化する目的関数のメトリック。
                値を取ることができます：MeanAbs()（デフォルト）、SumAbs()、および SumMeanAbs()。
        sol: 解を持つ構造
            solSpace: 全体の空間に対する目的関数の値を持つ行列
            objfunMin: 見つかった目的関数の最小値
            optOD: 光学厚さの最適値
            optParams: 他のパラメータの最適値
            optThickness: 厚さの最適値
            spectrumFit: dopt と xopt で得られた最適スペクトル
            spectrumExp: 実験スペクトル
            od: 探索された光学厚さの範囲
            p: 探索された多孔性の範囲
            beam: 使用された光の情報
```
