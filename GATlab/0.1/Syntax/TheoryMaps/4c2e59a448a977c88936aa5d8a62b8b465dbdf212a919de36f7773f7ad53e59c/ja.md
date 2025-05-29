TheoryMapsはGATのカテゴリにおける射です。TheoryMap X -> Yは多くの方法で考えることができます。

1. 「Yのすべてのモデルは、何らかの方法でXのモデルでもある」
2. Yへの「X型のフック」を提供する。
3. XはYの意味論の構文です。

AbsTheoryMapが実装すべき主なメソッドは次のとおりです：

  * dom, codom,
  * typemap: Ident（ドメイン内のAlgTypeConstructorの）からTypeInCtxへの辞書（TypeInCtxのTypeScopeは、キーに関連付けられた型コンストラクタのlocalcontextと構造的に同一でなければなりません）。
  * termmap: Ident（ドメイン内のAlgTermConstructorの）からTermInCtxへの辞書。（TrmInCtxのTypeScopeは、キーに関連付けられた項コンストラクタのlocalcontext + argsと構造的に同一でなければなりません。）

`typemap`と`termmap`の値がドメイン内のコンテキストと構造的に同一であるという要件は、最終的には緩和される可能性があります（順序の変更、追加の派生要素、未使用の引数の削除を許可するため）が、今のところはシンプルさのためにこれを要求します。
