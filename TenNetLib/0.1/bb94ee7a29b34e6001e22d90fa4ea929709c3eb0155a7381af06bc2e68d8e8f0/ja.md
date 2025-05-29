```
function CouplingModel(os::OpStrings{T1},
                       sites::Vector{Index{T2}};
                       merge::Bool = true,
                       maxdim::Int = typemax(Int),
                       mindim::Int = 1,
                       cutoff::Float64 = Float64_threashold(),
                       svd_alg::String = "divide_and_conquer",
                       chunksize::Int = 12) where {T1 <: Number, T2}
```

`CouplingModel`のコンストラクタは`os::OpStrings`と`sites::Vector{Index}`から構成されます。

#### 名前付き引数とそのデフォルト値:

  * `merge::Bool = true`。`true`の場合、同じ空間サポートを持つすべての項をマージし、より大きな仮想次元を生成します。そうでない場合、すべての項は仮想次元1を持ちます。
  * `maxdim::Int = typemax(Int)`: SVD切り捨て後の最大ボンド次元。
  * `mindim::Int = 1`: SVD切り捨て後の最小ボンド次元。
  * `cutoff::Float64 = Float64_Threshold()`: SVD切り捨てのカットオフ。
  * `svd_alg::String = "divide_and_conquer"`.
  * `chunksize::Int = 12`.

#### 例:

```
os = OpStrings()    
for j=1:N-1
    os += 1, "Sz" => j, "Sz" => j+1
    os += 0.5, "S+" => j, "S-" => j+1
    os += 0.5, "S-" => j, "S+" => j+1
end    
H = CouplingModel(os,sites)
```
