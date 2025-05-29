```
LsimWorkspace(sys::AbstractStateSpace, N::Int)
LsimWorkspace(sys::AbstractStateSpace, u::AbstractMatrix)
LsimWorkspace{T}(ny, nu, nx, N)
```

インプレース関数 [`lsim!`](@ref) で使用するためのワークスペースオブジェクトを生成します。`sys` はシミュレーションされる離散時間システムであり、`N` は時間ステップの数です。代わりに、入力 `u` を `N` の代わりに提供することもできます。注意: スレッドアプリケーションの場合、スレッドごとに1つのワークスペースオブジェクトを作成してください。
