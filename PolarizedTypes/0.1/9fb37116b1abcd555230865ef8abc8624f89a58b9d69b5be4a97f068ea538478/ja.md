```julia
struct CoherencyMatrix{B1, B2, T} <: StaticArraysCore.FieldMatrix{2, 2, T}
```

単一のベースラインのコヒーレンシーマトリックスで、ベースは `B1` と `B2` です。2つのベースは、各望遠鏡に使用されるフィードのタイプに対応し、`PolBasis` のサブタイプである必要があります。どのベースが実装されているかを確認するには、REPLで `subtypes(Rimes.PolBasis)` と入力してください。

円形ベースの場合、コヒーレンシーマトリックスのレイアウトは次のようになります。

```
RR* RL*
LR* RR*
```

これは次のように構築できます。

```julia-repl
c = CoherencyMatrix(RR, LR, RL, LL, CirBasis())
```

線形ベースの場合、コヒーレンシーマトリックスのレイアウトは次のようになります。

```
XX* XY*
YX* YY*
```

これは次のように構築できます。

```julia-repl
c = CoherencyMatrix(XX, YX, XY, YY, CirBasis())
```

混合（例：円形と線形ベース）の場合、コヒーレンシーマトリックスのレイアウトは次のようになります。

```
RX* RY*
LX* LY*
```

または、例えば、線形と円形の場合、コヒーレンシーマトリックスのレイアウトは次のようになります。

```
XR* XL*
YR* YL*
```

これらのコヒーレンシーマトリックスは次のように構築できます。

```julia-repl
# 円形と線形フィード、すなわち |R><X|
c = CoherencyMatrix(RX, LX, RY, LY, LinBasis(), CirBasis())
# 線形と円形フィード、すなわち |X><R|
c = CoherencyMatrix(XR, YR, XL, YL, LinBasis(), CirBasis())
```
