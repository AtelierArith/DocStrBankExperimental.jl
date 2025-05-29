```
module MethodInSrc
```

`MethodInSrc`は、関数呼び出しがモジュール内で定義されたメソッドにディスパッチされる（またはされない）ことを検証するために、テストスイートで使用するツールを提供します。これらは、より一般的なメソッドではなく、特化したメソッドが呼び出されることを確認するためのものです。（またはその逆。）

このモジュールは、`@isinsrc`、`@insrc`、`@ninsrc`、`@isinmodule`、`@inmodule`、および `@ninmodule`をエクスポートします。

`@isinsrc f(x)`は、`f(x)`のメソッドが`../src`の下に見つかった場合に`true`を返します。ただし、`f(x)`を評価することはありません。

`@insrc f(x)`は、`f(x)`のメソッドが`../src`の下に見つからない場合にエラーをスローします。それ以外の場合は、`f(x)`を評価します。

`@ninsrc`は、`@insrc`と同じですが、メソッドが`../src`の下にある場合にスローします。

最初の3つのマクロは、モジュールの「テスト」ディレクトリ内のファイルで使用することを意図しています。この場合、`@isinsrc f([x,...])`は、`f([x,...])`によって呼び出されるメソッドがモジュールの「src」ディレクトリで定義されている場合に`true`を返します。

`@isinmodule`、`@inmodule`、および `@ninmodule`のドキュメント文字列を参照してください。

## 例

型`MyPackage.AMatrix`は、要素がすべて`1`である正方行列を表します。`MyPackage`は、`::AMatrix`の効率的なメソッドで`Base.sum`を拡張します。`MyPackage`には、効率的な関数`prod(::AMatrix)`も含まれています。しかし、`Base.prod`を書くか、`import Base: prod`をするのを忘れてしまいました。したがって、`MyPackage.prod`は`Base.prod`の拡張ではありません。

### `@isinsrc`

`@isinsrc`を使用して、`sum`と`prod`の両方が`Base`関数を拡張していることを確認します。（`prod`はそうではありません！）

```julia
using MyPackage
using MethodInSrc
using Test

m = MyPackage.AMatrix{Int}(3)
@test @isinsrc sum(m)
@test @isinsrc prod(m)  # これは失敗します！
```

### `@insrc`、`@ninsrc`

2つのテストを書くのが面倒な場合は、`@insrc`を使用して、正しいメソッドがあることを確認し、別のテストでその正しさを確認します。

`@insrc`は、メソッドが`../src`に定義されていることを確認し、その後に式を評価します。ここでは、`MyPackage.prod`が異なる関数であることを知っていると仮定し、それをテストします。これらのテストはすべて合格します。

```julia
using MyPackage
using MethodInSrc
using Test

N = 3
m = MyPackage.AMatrix{Int}(N)

# `@insrc`は次の式を引数として取ることに注意してください。
# 私たちは関数呼び出しだけをテストする必要があります。
@test_throws ErrorException 1 == @insrc prod(m)   # これはメソッドを見つけます。
@test_throws ErrorException @insrc(prod(m)) == 1  # これもそうです。
@test 1 == @ninsrc prod(m)  # メソッドが一般的である場合にテストを行います。

# 次のメソッドは`../src`に見つかるため、式は評価されます。
@test N^2 == @insrc sum(m)
@test (@insrc sum(m)) == N^2
@test @insrc(MyPackage.prod(m)) == 1
```
