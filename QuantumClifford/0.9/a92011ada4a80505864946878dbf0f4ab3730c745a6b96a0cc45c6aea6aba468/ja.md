```julia
pftrajectories(
    circuit;
    trajectories,
    threads
) -> QuantumClifford.PauliFrame{QuantumClifford.Stabilizer{QuantumClifford.Tableau{Vector{UInt8}, LinearAlgebra.Adjoint{UInt64, Matrix{UInt64}}}}, Matrix{Bool}}

```

回路のパウリフレームシミュレーションを実行するための主要なメソッドです。より低レベルのアクセスについては他のメソッドを参照してください。

マルチスレッドはデフォルトで有効ですが、`threads=false`を設定することで無効にできます。マルチスレッドを使用したい場合は、複数のスレッドを有効にしてJuliaを起動することを忘れないでください。例えば、`julia -t4`のようにします。

関連情報: [`mctrajectories`](@ref), [`petrajectories`](@ref)
