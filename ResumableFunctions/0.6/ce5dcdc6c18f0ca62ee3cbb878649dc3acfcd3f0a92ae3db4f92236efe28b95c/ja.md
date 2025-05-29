有限状態機械における関数定義を変換するマクロ：

  * イテレータインターフェースを実装し、内部状態を格納するために使用される新しい `mutable struct` を定義します。
  * この新しい型を呼び出し可能にし、以下の特性を持たせます：

      * 初期関数定義からの文を実装しますが；
      * `@yield` 文で返し；
      * 再度呼び出されたときに `@yield` 文の後から続行します。
  * 初期関数定義の呼び出し規約を尊重し、新しい型のオブジェクトを返すコンストラクタ関数を定義します。

要素の型と長さが知られている場合、結果のイテレータは次のように効率的にすることができます：

  * イテレータの長さ（もし知られている場合）を指定するために `length=ex` を使用します。例えば：   @resumable length=ex function f(x); body; end ここで `ex` は `f` の引数を含む任意の式です。
  * イテレータの要素型を指定するために `function f(x)::T` を使用します。

# 拡張

```julia
julia> @resumable length=n^2 function f(n)::Int
         for i in 1:n^2
           @yield i
         end
       end
f (generic function with 2 methods)

julia> collect(f(3))
9-element Vector{Int64}:
 1
 2
 3
 4
 5
 6
 7
 8
 9
```
