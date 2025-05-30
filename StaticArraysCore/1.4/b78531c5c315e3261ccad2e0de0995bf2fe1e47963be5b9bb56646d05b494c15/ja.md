```
abstract FieldMatrix{N1, N2, T} <: FieldArray{Tuple{N1, N2}, 2}
```

この型を継承することで、自分自身のランク2テンソル型を簡単に作成できます。`FieldMatrix`は自動的に`getindex`と`setindex!`を適切に定義します。不変の`FieldMatrix`は、同様の長さと要素型の`SMatrix`と同じくらいのパフォーマンスを持ち、可変の`FieldMatrix`は`MMatrix`と同様の動作をします。

`FieldMatrix`の任意のサブタイプのフィールドは、独自の`getindex`を実装することを望まない限り、列優先順序で定義する必要があります。

要素型に対してパラメトリックな`FieldMatrix`を定義する場合は、`FieldVector`の例のように`similar_type`を定義することを検討してください。

# 例

```
struct Stress <: FieldMatrix{3, 3, Float64}
    xx::Float64
    yx::Float64
    zx::Float64
    xy::Float64
    yy::Float64
    zy::Float64
    xz::Float64
    yz::Float64
    zz::Float64
end
```

`FieldMatrix`の任意のサブタイプのフィールドは、列優先順序で定義する必要があります。これは、リテラル`FieldMatrix`のコンストラクタのフォーマットが混乱を招く可能性があることを意味します。例えば、

```
sigma = Stress(1.0, 2.0, 3.0,
               4.0, 5.0, 6.0,
               7.0, 8.0, 9.0)

3×3 Stress:
 1.0  4.0  7.0
 2.0  5.0  8.0
 3.0  6.0  9.0
```

は、複数の引数のフォーマットが示唆するものの転置を返します。明確にするために、代わりに次のように使用することを検討してください。

```
sigma = Stress(SA[1.0 2.0 3.0;
                  4.0 5.0 6.0;
                  7.0 8.0 9.0])
```
