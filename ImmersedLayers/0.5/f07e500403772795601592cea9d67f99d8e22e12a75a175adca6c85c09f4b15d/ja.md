```
vecfield_helmholtz!(v::Edges{Primal},curlv::Nodes{Dual},divv::Nodes{Primal},dv::VectorData,vp::Union{Edges{Primal},Nothing},base_cache::BasicILMCache,veccache::VectorFieldCache)
```

マスクされたカール場 `curlv` ($\overline{\nabla\times\mathbf{v}}$)、ダイバージェンス場 `divv` ($\overline{\nabla\cdot\mathbf{v}}$)、表面ベクトルジャンプ `dv` ($[\mathbf{v}]$)、および追加の回転のない、ダイバージェンスのないベクトル場 `vp` からベクトル場 `v` を復元します。これはヘルモルツ分解から得られます。

$$
\mathbf{v} = \nabla\times\psi + \nabla\phi + \mathbf{v}_p
$$

ここで、$\psi$ は次の方程式の解です。

$$
L_n\overline{\psi} = -\overline{\nabla\times\mathbf{v}} - R_n\mathbf{n}\times[\mathbf{v}]
$$

ここで、$\phi$ は次の方程式の解です。

$$
L_c\overline{\phi} = \overline{\nabla\cdot\mathbf{v}} + R_c\mathbf{n}\cdot[\mathbf{v}]
$$

重要な点は、`curlv` はベクトル場のマスクされたカールであり、マスクされたベクトル場のカールではないということです。後者から前者を得るには、[`masked_curlv_from_curlv_masked!`](@ref) を使用します。同様に、`divv` もベクトル場のマスクされたダイバージェンスであり、マスクされたベクトル場のダイバージェンスではありません。これには [`masked_divv_from_divv_masked!`](@ref) を使用できます。

回転のない、ダイバージェンスのないベクトル場 `vp` を指定するには、単にタプルを提供することもできます。例えば、均一なベクトル場を指定するために `(1.0,0.0)` のようにします。
