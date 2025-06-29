成長ベースのスクリーニングで使用されるパラメータを表す型。

  * `num_genes`: スクリーニングでターゲットとされる遺伝子の数
  * `coverage`: 各遺伝子あたりのガイドの数
  * `representation`: 各ガイドを持つ細胞の数。`representation=10`は、トランスフェクション中にガイドの10倍の細胞が存在することを意味します。トランスフェクション後の各ガイドあたりの実際の細胞数は、MOIに応じて少なくなります。
  * `moi`: スクリーニングの感染の重複度、$\lambda$。これをトランスフェクション中のポアソン過程としてモデル化します（[`Crispulator.transfect`](@ref）を参照）。

    !!! note
        我々は**複数の感染**をモデル化しません。MOIが適切に選択され、細胞の半分未満が任意のウイルスによってトランスフェクトされると仮定します。すなわち、$\lambda \lt 0.5$であり、単一のトランスフェクションが発生した細胞のみを選択します：

        $$
        P(x = 1; Poisson(λ))
        $$

        $$
        \lambda = 0.25
        $$

        の場合、これは細胞の数の約19.5\%（`num_genes` * `coverage` * `representation`）に相当します。
  * `seq_depth`: ガイドの数の整数倍としてのシーケンシング深度。すなわち、`seq_depth=10`は`10 * num_genes * coverage`リードに相当します。
  * `bottleneck_representation`: 成長スクリーニングにおいて、どれだけのボトルネックが適用されるか。これは、細胞のプールをパッセージングする際に保持される最小細胞数です。これはガイドの数の整数倍として表現されます。
  * `num_bottlenecks`: 成長スクリーニングにおいて、いくつのボトルネックが適用されるか。これは成長スクリーニング中のパッセージの整数回数です。
  * `noise`: 各パッセージの前に、各細胞の理論的表現型が、このパラメータによって決定される標準偏差σを持つ正規ノイズ分布と畳み込まれます。これはサブサンプリングのノイズの期待に基づいて設定する必要があります。
