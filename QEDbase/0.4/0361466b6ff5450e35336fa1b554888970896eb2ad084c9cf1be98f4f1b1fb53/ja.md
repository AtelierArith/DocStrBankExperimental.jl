散乱過程の定義のための抽象基本型です。これはプロセスインターフェースのルート型であり、`AbstractProcessDefinition`のすべてのサブタイプが少なくとも以下を実装することを前提としています。

```Julia
incoming_particles(proc_def::AbstractProcessDefinition)
outgoing_particles(proc_def::AbstractProcessDefinition)
```

これらはそれぞれ、入射粒子と出射粒子のタプルを返します。

`AbstractProcessDefinition`はまた、その粒子のスピンおよび偏光情報を含むことが期待されています。そのために、以下の関数をオーバーロードすることができます。

```Julia
incoming_spin_pols(proc_def::AbstractProcessDefinition)
outgoing_spin_pols(proc_def::AbstractProcessDefinition)
```

これらは[`AbstractSpinOrPolarization`]のタプルを返さなければならず、順序はプロセスの粒子の順序と一致しなければなりません。デフォルトの実装が提供されており、すべての[`is_fermion`](@ref)粒子に対して[`AllSpin`](@ref)を、すべての[`is_boson`](@ref)粒子に対して[`AllPolarization`](@ref)を仮定しています。

!!! note "パフォーマンス"
    これらの関数がコンパイル時に既知の値を返す場合、派生関数のパフォーマンスに非常に有益です。


これらのスピンおよび偏光関数に加えて、以下の関数が自動的に定義されます。

```Julia
multiplicity(proc_def::AbstractProcessDefinition)
incoming_multiplicity(proc_def::AbstractProcessDefinition)
outgoing_multiplicity(proc_def::AbstractProcessDefinition)
```

これらは、プロセスに対して考慮すべきスピンおよび偏光の組み合わせの数を返します。詳細については、関数のドキュメントを参照してください。

さらに、散乱確率および微分断面積を計算するために、以下のインターフェース関数を`CustomProcess<:AbstractProcessDefinition`、`CustomModel<:AbstractModelDefinition`、および`CustomPhaseSpaceLayout<:AbstractPhaseSpaceLayout`のすべての組み合わせに対して実装する必要があります。

```Julia
    _incident_flux(psp::InPhaseSpacePoint{CustomProcess,CustomModel})

    _matrix_element(psp::PhaseSpacePoint{CustomProcess,CustomModel})

    _averaging_norm(proc::CustomProcess)

    _is_in_phasespace(psp::PhaseSpacePoint{CustomProcess,CustomModel})

    _phase_space_factor(psp::PhaseSpacePoint{CustomProcess,CustomModel,CustomPhaseSpaceLayout})
```

総確率および断面積の計算を可能にするために、以下の実装はオプションです。

```Julia

    _total_probability(psp::PhaseSpacePoint{CustomProcess,CustomModel,CustomPhaseSpaceLayout})

```
