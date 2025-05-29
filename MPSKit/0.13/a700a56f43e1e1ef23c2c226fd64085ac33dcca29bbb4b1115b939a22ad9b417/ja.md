```
exact_diagonalization(H::FiniteMPOHamiltonian;
                      sector=first(sectors(oneunit(physicalspace(H, 1)))),
                      len::Int=length(H), num::Int=1, which::Symbol=:SR,
                      alg=Defaults.alg_eigsolve(; dynamic_tols=false))
                        -> vals, state_vecs, convhist
```

`FiniteMPOHamiltonian`に対して正確な対角化を行い、最大ランクの`FiniteMPS`として固有ベクトルを見つけるために、[`KrylovKit.eigsolve`](@extref)を使用します。これは、実質的に密な固有ベクトルと同等です。

### 引数

  * `H::FiniteMPOHamiltonian`: 対角化するハミルトニアン。

### キーワード引数

  * `sector=first(sectors(oneunit(physicalspace(H, 1))))`: 固有ベクトルの総電荷で、デフォルトでは自明に選択されます。
  * `len::Int=length(H)`: 系の長さ。
  * `num::Int=1`: 見つける固有ベクトルの数。
  * `which::Symbol=:SR`: 見つける固有値の種類、[`KrylovKit.eigsolve`](@extref)を参照してください。
  * `alg=Defaults.alg_eigsolve(; dynamic_tols=false)`: 使用する対角化アルゴリズム、[`KrylovKit.eigsolve`](@extref)を参照してください。

!!! note "有効な `sector` 値"
    固有ベクトルの総電荷は、各固有ベクトルの最も左の仮想空間として帯電した補助空間を追加することによって課されます。具体的には、[`FiniteMPS`](@ref)コンストラクタに`left=Vect[typeof(sector)](sector => 1)`を渡すことで実現されます。そのため、対応する固有状態が有効な融合チャネルを持つ有効な`sector`値（すなわち、`sector`値）は、系内のすべての物理空間の融合の双対に現れるものだけです。

