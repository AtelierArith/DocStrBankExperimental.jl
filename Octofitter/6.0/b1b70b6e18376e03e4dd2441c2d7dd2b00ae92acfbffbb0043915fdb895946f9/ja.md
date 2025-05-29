```
@planet [planet_name] [Orbit_Type] begin
    [prior_1] ~ [UnivariateDistribution]
    [prior_2] ~ [UnivariateDistribution]
    calculation_3 = [planet_name].[prior_1] + [planet_name].[prior_2] + [system.variable_x]
end [likelihood_objects...]
```

`planet_name`という名前の惑星モデルを生成します。現在のスコープに`[planet_name]`という名前の変数が作成されます。`Orbit_Type`はPlanetOrbits.jlからの軌道パラメータ化を指定します。選択した軌道タイプに必要なすべての入力変数を提供する必要があります（PlanetOrbits.jlのドキュメントを参照）。その後、変数の割り当てのブロックがあります。`~`を持つ変数は、右辺によって与えられた事前分布を持つ自由変数です（Distributions.jlのUnivariateDistributionまたは`KDEDist`）。計算された量も許可されます。これらは、惑星名の後にドットと変数名を続けて他の変数を参照することができます。同一システム内の他の惑星からの変数にはアクセスできません。現在のローカルスコープ内の他の変数にはアクセスできますが、これらのバインディングは一度だけ解決されることが保証されています。計算式で非定数のグローバル変数を使用すると、パフォーマンスが低下する可能性があることに注意してください。最後に、惑星モデルは、ゼロまたはそれ以上の尤度オブジェクトを供給することによってデータに条件付けることができます。
