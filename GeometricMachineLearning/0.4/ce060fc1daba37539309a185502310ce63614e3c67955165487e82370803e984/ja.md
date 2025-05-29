```
HRedSys
```

`HRedSys`は、縮小されたシステムに基づいて完全なシステムの再構成された動力学を計算します。オプションで、FOMソリューションと比較することもできます。

2つの異なるコンストラクタを使用して呼び出すことができます。

# コンストラクタ

標準のコンストラクタは次のとおりです：

```julia
HRedSys(N, n; encoder, decoder, v_full, f_full, v_reduced, f_reduced, parameters, tspan, tstep, ics, projection_error)
```

ここで 

  * `encoder`: 関数 $\mathbb{R}^{2N}\mapsto{}\mathbb{R}^{2n}$
  * `decoder`: （微分可能な）関数 $\mathbb{R}^{2n}\mapsto\mathbb{R}^{2N}$
  * `v_full`: GeometricIntegratorsと同様に定義された（微分可能な）写像。
  * `f_full`: GeometricIntegratorsと同様に定義された（微分可能な）写像。
  * `v_reduced`: GeometricIntegratorsと同様に定義された（微分可能な）写像。
  * `f_reduced`: GeometricIntegratorsと同様に定義された（微分可能な）写像。
  * `integrator`: 縮小されたシステムを統合するために使用されます。
  * `parameters`: ベクトル場をパラメータ化するNamedTuple（完全な*ベクトル*場と縮小された*ベクトル*場の両方に対して同じ）。
  * `tspan`: 統合が行われる時間間隔の開始点と終了点を指定するタプル `(t₀, tₗ)`。
  * `tstep`: 時間ステップ
  * `ics`: 大きなシステムの初期条件。

もう一つの、より便利なコンストラクタは次のとおりです：

```julia
HRedSys(odeensemble, encoder, decoder) 
```

ここで `odeensemble` は `HODEEnsemble` または `HODEProblem` であることができます。`encoder` と `decoder` はニューラルネットワークでなければなりません。このコンストラクタを使用すると、キーワード引数 `integrator` を介して統合器を渡すこともできます。デフォルトは `ImplicitMidpoint()` です。内部的には、縮小されたベクトル場を構築するために関数 [`build_v_reduced`](@ref) と [`build_f_reduced`](@ref) が呼び出されます。
