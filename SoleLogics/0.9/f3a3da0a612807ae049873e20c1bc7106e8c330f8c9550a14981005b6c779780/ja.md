```
abstract type Formula <: Syntactical end
```

論理式のための抽象型。`Formula`の例には、`SyntaxLeaf`（例えば、`Atom`や`Truth`値）、`AbstractSyntaxStructure`（例えば、`SyntaxTree`や`LeftmostLinearForm`）および`TruthTable`（構文構造に追加の[メモ化](https://en.wikipedia.org/wiki/Memoization)構造を関連付ける強化された表現で、[モデル検査](https://en.wikipedia.org/wiki/Model_checking)時に計算時間を節約できる）があります。

任意の式は、[`tree`](@ref)を介してその[`SyntaxTree`](@ref)表現に変換でき、その[`height`](@ref)を計算でき、構文[`tokens`](@ref)、[`atoms`](@ref)などを照会できます... それは、[`syntaxstring`](@ref)表現から[`parseformula`](@ref)を介して解析できます。

他に[`tree`](@ref)、[`AbstractSyntaxStructure`](@ref)、[`SyntaxLeaf`](@ref)も参照してください。
