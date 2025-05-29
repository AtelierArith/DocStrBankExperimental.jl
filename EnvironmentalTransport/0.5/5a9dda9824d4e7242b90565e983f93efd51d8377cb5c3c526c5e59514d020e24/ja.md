```julia
Puff(
    di::EarthSciMLBase.DomainInfo;
    name
) -> ModelingToolkit.ODESystem

```

流体速度場内で物質の「パフ」または粒子を輸送するラグランジュモデルを作成します。

モデルの境界はDomainInfo引数によって設定されます。モデルは地面とモデルの底および上部に境界を設定し、パフがそれらの境界を越えるのを防ぎます。パフが水平境界の1つに達すると、シミュレーションは停止します。
