structure*factor(particle*centres::Vector, distances::AbstractVector)

1つの粒子の配置から各方向の構造因子を計算します。多くの粒子の配置を使用するには、この関数を各配置に対して呼び出し、ペア相関の平均を取ります。
