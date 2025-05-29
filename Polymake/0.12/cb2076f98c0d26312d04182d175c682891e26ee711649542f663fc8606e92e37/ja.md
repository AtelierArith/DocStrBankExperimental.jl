```
@pm polymakeapp.function_name{テンプレート, パラメータ}(args)
```

このマクロは以下のために使用できます。

  * `polymake` ビッグオブジェクト（ポリトープなど）を作成する
  * 特定のテンプレートパラメータを持つ `polymake` 関数を呼び出す。

マクロに渡される式は次のいずれかでなければなりません：

  * `polymake` オブジェクトの完全修飾名（すなわち、`polymake` アプリケーションの**小文字**の名前で始まる）、または
  * `{ ... }` で囲まれたテンプレートパラメータを持つ関数。

# 例

```jldoctest
julia> P = @pm polytope.Polytope{QuadraticExtension}(POINTS=[1 0 0; 0 1 0])
type: Polytope<QuadraticExtension<Rational>>

POINTS
1 0 0
0 1 0



julia> @pm common.convert_to{Float}(P)
type: Polytope<Float>

POINTS
1 0 0
0 1 0


CONE_AMBIENT_DIM
3



julia> @pm tropical.Polytope{Max}(POINTS=[1 0 0; 0 1 0])
type: Polytope<Max, Rational>

POINTS
0 -1 -1
0 1 0



```

!!! 注意     `@pm` マクロ内の式は構文的に解析されるため、有効な `julia` 式でなければなりません。ただし、テンプレートパラメータは **julia** で定義されている必要はありませんが、`polymake` プロパティタイプの有効な名前でなければなりません。ネストされた型（例えば `{QuadraticExtension{Rational}}`）も許可されています。
