```
BodemagWorkspace(sys::LTISystem, N::Int)
BodemagWorkspace(sys::LTISystem, ω::AbstractVector)
BodemagWorkspace(R::Array{Complex{T}, 3}, mag::Array{T, 3})
BodemagWorkspace{T}(ny, nu, N)
```

`bodemag!`(@ref) 関数で使用するためのワークスペースオブジェクトを生成します。`N` は周波数点の数であり、代わりに入力 `ω` を `N` の代わりに提供することができます。注意: スレッドを使用するアプリケーションの場合、スレッドごとに1つのワークスペースオブジェクトを作成してください。

# 引数:

  * `mag`: 出力配列 ∈ 𝐑(ny, nu, nω)
  * `R`: 周波数応答配列 ∈ 𝐂(ny, nu, nω)
