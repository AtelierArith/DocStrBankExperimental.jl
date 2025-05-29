```
MPDeC(K; [nodes = :gausslobatto, linsolve = ..., small_constant = ...])
```

生産-消滅システムのための任意の次数の修正パタンカール-ルンゲ-クッタ法のファミリーです。このファミリーの各メンバーは、K次の精度を持ち、無条件に正の値を保持し、線形暗黙的な適応型一段階法です。整数Kは、2 ≤ K ≤ 10を満たすように選択する必要があります。利用可能なノードの選択肢はラグランジュノードまたはガウス-ロバットノードであり、後者がデフォルトです。これらの方法は、1回の補正ステップを少なくして得られた数値解を使用して誤差を推定するための低次近似として、適応的な時間ステッピングをサポートします。MPDeCスキームは、トルロとエフナーによって（2020年）自律的な保存的生産-消滅システムのために導入され、トルロ、エフナー、ラノチャによって（2022年）さらに調査されました。

非保存的な生産-消滅システムに対しては、[`MPE`](@ref)に類似した直接的な拡張を使用します。非自律的な微分方程式に適用され、一般的な積分ノードを使用したDeCスキームの一般的な議論は、オングとスピテリによって（2020年）行われています。

MPDeCメソッドは、[`PDSProblem`](@ref)または[`ConservativePDSProblem`](@ref)の特別な構造を必要とします。

オプションで、キーワード引数`linsolve`として[LinearSolve.jl](https://github.com/SciML/LinearSolve.jl)からアルゴリズムを渡すことで使用する線形ソルバーを選択できます。また、すべてのパタンカール重みの分母に追加され、ゼロ除算を避けるためのパラメータ`small_constant`を選択することもできます。値を明示的に渡すことができますが、そうでない場合、`small_constant`は倍精度計算で`1e-300`に設定されるか、使用される浮動小数点型の`floatmin`に設定されます。

## 参考文献

  * Davide Torlo and Philipp Öffner. "任意の高次、保存的かつ正の値を保持するパタンカール型遅延補正スキーム。" Applied Numerical Mathematics 153 (2020): 15-34. [DOI: 10.1016/j.apnum.2020.01.025](https://doi.org/10.1016/j.apnum.2020.01.025)
  * Davide Torlo, Philipp Öffner, and Hendrik Ranocha. "正の値を保持するパタンカール型スキームに関する問題。" Applied Numerical Mathematics 182 (2022): 117-147. [DOI: 10.1016/j.apnum.2022.07.014](https://doi.org/10.1016/j.apnum.2022.07.014)
  * Benjamin W. Ong and Raymond J. Spiteri. "常微分方程式のための遅延補正法。" Journal of Scientific Computing 83 (2020): Article 60. [DOI: 10.1007/s10915-020-01235-8](https://doi.org/10.1007/s10915-020-01235-8)
