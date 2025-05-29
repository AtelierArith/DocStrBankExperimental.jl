```
struct Physics{T,F,M,Tu,E,D,BI}
    time::T
    fluid::F
    momentum::M 
    turbulence::Tu 
    energy::E
    domain::D
    boundary_info::BI
end
```

XCALibreのパラメトリックPhysics型は、ユーザーレベルのAPI用です。また、フローソルバーのディスパッチにも使用されます。

### フィールド

  * 'time::Union{Steady, Transient}'   – ユーザー提供の時間モデル。
  * 'fluid::AbstractFluid'  – ユーザー提供の`Fluid`モデル。
  * 'momentum'  – モーメンタムモデル。現在、これは`Physics`コンストラクタによって自動生成されています。
  * 'turbulence::AbstractTurbulenceModel'  – ユーザー提供の`Turbulence`モデル。
  * 'energy:AbstractEnergyModel'  – ユーザー提供の`Energy`モデル。
  * 'domain::AbstractMesh '  – ユーザー提供の`Mesh`。Physicsオブジェクトを構築する前に、ターゲットデバイスに適応させる必要があります。
  * 'boundary*info::boundary*info'  – メッシュ境界情報。`Physics`コンストラクタによって自動生成されます。
