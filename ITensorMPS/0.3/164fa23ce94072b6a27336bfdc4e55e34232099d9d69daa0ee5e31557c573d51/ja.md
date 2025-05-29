```
expect(psi::MPS, op::AbstractString...; kwargs...)
expect(psi::MPS, op::Matrix{<:Number}...; kwargs...)
expect(psi::MPS, ops; kwargs...)
```

MPS `psi` と単一の演算子名が与えられた場合、MPS の各サイトにおける演算子の期待値のベクトルを返します。

複数の演算子名が提供された場合、期待値ベクトルのタプルを返します。

演算子名のコンテナが提供された場合、名前を期待値のベクトルに置き換えた同じタイプのコンテナを返します。

# オプションのキーワード引数

  * `sites = 1:length(psi)`: 指定された範囲内のサイトに対してのみ期待値を計算します

# 例

```julia
N = 10

s = siteinds("S=1/2", N)
psi = random_mps(s; linkdims=8)
Z = expect(psi, "Sz") # すべてのサイトに対して計算
Z = expect(psi, "Sz"; sites=2:4) # サイト 2,3,4 に対して計算
Z3 = expect(psi, "Sz"; sites=3)  # サイト 3 のみ計算 (出力はスカラーになります)
XZ = expect(psi, ["Sx", "Sz"]) # すべてのサイトに対して Sx と Sz を計算
Z = expect(psi, [1/2 0; 0 -1/2]) # expect(psi,"Sz") と同じ

s = siteinds("Electron", N)
psi = random_mps(s; linkdims=8)
dens = expect(psi, "Ntot")
updens, dndens = expect(psi, "Nup", "Ndn") # 複数の演算子を渡す
```
