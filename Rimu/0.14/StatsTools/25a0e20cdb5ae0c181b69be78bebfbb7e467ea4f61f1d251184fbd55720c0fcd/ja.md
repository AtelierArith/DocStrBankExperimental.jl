```
replica_fidelity(df::DataFrame; p_field = :hproj, skip = 0)
replica_fidelity(sim::PMCSimulation; kwargs...)
```

平均係数ベクトルと`p_field`で定義された射影子の忠実度を、解決によって返される[`PMCSimulation`](@ref Main.Rimu.PMCSimulation)または`DataFrame`から、レプリカ`_1`と`_2`を使用して計算します。別々の時系列の平均の比率に対してブロッキング分析を行うために[`ratio_of_means`](@ref)を呼び出し、[`RatioBlockingResult`](@ref)を返します。時系列の最初の`skip`ステップはスキップされます。

状態`|ψ⟩`と`|ϕ⟩`の忠実度は次のように定義されます。

$$
F(ψ,ϕ) = \frac{|⟨ψ|ϕ⟩|^2}{⟨ψ|ψ⟩⟨ϕ|ϕ⟩} .
$$

具体的には、`replica_fidelity`は次を計算します。

$$
F(\mathbf{v},⟨\mathbf{c}⟩) =
    \frac{⟨(\mathbf{c}_1⋅\mathbf{v})(\mathbf{v}⋅\mathbf{c}_1)⟩}
    {⟨\mathbf{c}_1⋅\mathbf{c}_1⟩} ,
$$

ここで`v`は`p_field`で指定された射影子であり、二ノルムで単位に正規化されていると仮定されます（すなわち、`v⋅v == 1`）、$\mathbf{c}_1$と$\mathbf{c}_2$は二つのレプリカ係数ベクトルです。
