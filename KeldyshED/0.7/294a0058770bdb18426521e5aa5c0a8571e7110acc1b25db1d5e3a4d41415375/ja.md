```julia
EDCore(
    hamiltonian::KeldyshED.Operators.OperatorExpr{S<:Number},
    soi::KeldyshED.Hilbert.SetOfIndices;
    symmetry_breakers
) -> KeldyshED.EDCore

```

与えられたハミルトニアンをブロック対角形式に縮小し、対角化します。

このコンストラクタは、[`autopartition procedure`](@ref autopartition) と QR アルゴリズムを使用してブロックを対角化します。ハミルトニアンの不変部分空間は、提供されたセット `soi` からの複合インデックスを持つすべての生成および消滅演算子が1つの部分空間を別の部分空間にマッピングするように選択されます。

ハミルトニアンと不変部分空間を共有する必要がある演算子式のオプションリスト（`symmetry_breakers`）を渡すことが可能です。これらの演算子はハミルトニアンのいくつかの対称性を破る可能性があるため、それらを考慮に入れることで、より洗練された部分空間の分割とブロック構造が得られる場合があります。
