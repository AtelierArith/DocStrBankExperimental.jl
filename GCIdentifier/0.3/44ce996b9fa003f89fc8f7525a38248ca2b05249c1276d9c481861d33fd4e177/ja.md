```
find_missing_groups_from_smiles(smiles::String, groups;max_group_size = nothing, environment=false, reduced=false)
```

SMILES文字列とグループリスト（`groups::Vector{GCPair}`）を与えると、`groups`内でカバーされていない原子をカバーできる潜在的なグループのリスト（`new_groups::Vector{GCPair}`）を返します。`groups`ベクターが提供されていない場合、分子のすべての可能なグループを生成します。

重い原子を大きなグループに結合する際に、いくつかのヒューリスティックがコードに組み込まれています：

1. 炭素原子が別の炭素原子に結合している場合、炭素のうち1つだけが環にある場合を除き、それらはグループに結合されません。
2. 他の原子の組み合わせはすべて許可されます。

最初のヒューリスティックの背後にある論理は、隣接する原子が類似の電気陰性度を持つ場合、お互いの特性に大きな影響を与えないためです。そのため、グループに結合されません。将来的には、このアプローチを拡張して、同じグループに結合できる原子を決定するためにHNMRデータを使用することができるかもしれません。

オプションの引数：

  * `max_group_size::Int`: 生成されるグループ内の原子の最大数。`nothing`の場合、最大サイズは中心原子が結合している原子の数になります。
  * `environment::Bool`: trueの場合、グループのSMARTSにはそのグループが存在する環境に関する情報が含まれます。たとえば、ペンタンの場合、環境がfalseであれば、CH2グループは1つだけになりますが、環境がtrueであれば、CH3に結合した1つと別のCH2に結合した1つの2つのCH2グループがあります。
  * `reduced::Bool`: trueの場合、`max_group_size`に基づいて分子を表現するために必要な最小数のグループが生成されます。falseの場合、すべての可能なグループが生成されます。

## 例

```julia
julia> find_missing_groups_from_smiles("CC(=O)O")
7-element Vector{GCIdentifier.GCPair}:
 GCIdentifier.GCPair("[CX4;H3;!R]", "CH3")
 GCIdentifier.GCPair("[CX3;H0;!R]", "C=")
 GCIdentifier.GCPair("[OX1;H0;!R]", "O=")
 GCIdentifier.GCPair("[OX2;H1;!R]", "OH")
 GCIdentifier.GCPair("[CX3;H0;!R](=[OX1;H0;!R])", "C=O=")
 GCIdentifier.GCPair("[CX3;H0;!R]([OX2;H1;!R])", "C=OH")
 GCIdentifier.GCPair("[CX3;H0;!R](=[OX1;H0;!R])([OX2;H1;!R])", "C=O=OH")
```
