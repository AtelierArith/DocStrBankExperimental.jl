`LocallyGarsideMonoid{T}` は、局所的ガーサイドモノイドの抽象型であり、ここで `T` はシンプルの型です。そのようなモノイド `M` は、シンプルな `a,b` に対して次の関数を実装する必要があります。

  * `one(M)`
  * `isleftdescent(M,a,i::Int)`  は `M.atoms[i]≼ a` かどうか
  * `isrightdescent(M,a,i::Int)` は `a≽ M.atoms[i]` かどうか
  * `isrightascent(M,a,i::Int)`  は `a*M.atoms[i]` がシンプルかどうか
  * `*(M,a,b)`  は `a*b` がシンプルな場合、シンプル `a*b` を返します
  * `\(M,a,b)` は `a≼ b` の場合、シンプル `a` を返します
  * `/(M,a,b)`  は `a≽ b` の場合、シンプル `a/b` を返します
