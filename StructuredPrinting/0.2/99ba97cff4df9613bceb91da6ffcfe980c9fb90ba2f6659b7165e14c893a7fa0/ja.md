```
Options(;
    print_obj = Returns(true),
    highlight = Returns(false),
    recurse = x -> !any(y -> x isa y, (UnionAll, DataType)),
    custom = x -> "",
    print_type::Bool = false,
    recursion_depth::Int = 1000,
    max_type_depth::Int = 3
)

`@structured_print`の印刷オプション:

  * `print_obj` は、オブジェクト（およびおそらく型）を印刷するかどうかを示す `Bool` を返す呼び出し可能な関数です。
  * `highlight` は、オブジェクト（およびおそらく型）を強調表示するかどうかを示す `Bool` を返す呼び出し可能な関数です。
  * `recurse` は、印刷がこのオブジェクトにさらに再帰するかどうかを示す `Bool` を返す呼び出し可能な関数です。デフォルトは `x -> !any(y -> x isa y, (UnionAll, DataType))` に設定されています。
  * `custom` は、印刷された文字列を追加する空の文字列を返す呼び出し可能な関数です。
  * `print_type`: オブジェクトの型を印刷するかどうかを示す `Bool` を返す呼び出し可能な関数です。
  * `recursion_depth`: 再帰を停止する深さを示す Int です。
  * `max_type_depth`: 深さ制限付き型印刷に使用される Int です。

## 例

```

julia struct Leaf{T} end

struct Branch{A,B,C}     leafA::A     leafB::B     leafC::C end

struct Tree{A,B,C}     branchA::A     branchB::B     branchC::C end

t = Tree(     Branch(Leaf{(:A1, :L1)}(), Leaf{(:B1, :L2)}(), Leaf{(:C1, :L3)}()),     Branch(Leaf{(:A2, :L1)}(), Leaf{(:B2, :L2)}(), Leaf{(:C2, :L3)}()),     Branch(Leaf{(:A3, :L1)}(), Leaf{(:B3, :L2)}(), Leaf{(:C3, :L3)}()), )

using StructuredPrinting

# 構造体を単独で印刷

@structured_print t

# 型を強調表示して構造体を印刷

@structured*print t Options(;print*obj= x -> x isa typeof(t.branchB))

# 型のタプルを強調表示して構造体を印刷

@structured*print t Options(;print*obj= x -> any(y-> x isa y, (typeof(t.branchB), typeof(t.branchA)))) ```
