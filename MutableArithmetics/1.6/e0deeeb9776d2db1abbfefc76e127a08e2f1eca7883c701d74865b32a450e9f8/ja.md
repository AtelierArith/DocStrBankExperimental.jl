```
operate(op::Function, args...)
```

`op(args...)`の結果に等しいオブジェクトを返します。このオブジェクトは、引数に影響を与えることなく、MultableArithmetics APIを通じて変更可能です。

デフォルトでは：

  * `operate(+, x)`および`operate(+, x)`は`copy_if_mutable(x)`にリダイレクトされるため、可変型`T`は単項演算子`+(x::T) = x`および`*(x::T) = x`から同じインスタンスを返すことができます。
  * `operate(+, args...)`（および`operate(-, args...)`、`operate(*, args...)`）は、`length(args)`が2以上（または演算が`-`の場合）であれば`+(args...)`（および`-(args...)`、`*(args...)`）にリダイレクトされます。

`op`が可変引数に対して改善できる実装を持つ`Base`関数である場合、`operate(op, args...)`は`op(args...)`にリダイレクトするのではなく、MutableArithmetics APIに依存するこのパッケージ内の実装を持つ可能性があります。これは例えば以下のケースです：

  * `Base.sum`の場合、
  * `LinearAlgebra.dot`の場合、
  * 行列-行列積および行列-ベクトル積の場合。

したがって、可変引数の場合、`op(args...)`の代わりに`operate(op, args...)`を呼び出すことでパフォーマンスの利点があるかもしれません。

## 例

可変型`T`に対して、以下が定義されている場合：

```julia
function Base.:*(a::Bool, x::T)
    return a ? x : zero(T)
end
```

`operate(*, a, x)`は、`operate`の引数に影響を与える`x`のインスタンスを返します。したがって、以下のメソッドを実装する必要があります。

```julia
function MA.operate(::typeof(*), a::Bool, x::T)
    return a ? MA.mutable_copy(x) : zero(T)
end
```
