```
@insrc f([x, y,...])
```

式を評価します。呼び出されたメソッドがテストが実行されているモジュールのソースディレクトリ（"src"）で定義されている場合はそうします。そうでない場合は、`ErrorException`をスローします。

`@insrc`はモジュールの"test"ディレクトリ内から呼び出されることを意図しています。srcディレクトリは"test/../src"を介して見つけられます。

### 例

`MyPackage`に対して`sum`のメソッドが定義されていることを確認します。

```julia
using MyPackage
using MethodInSrc
using Test

m = MyPackage.AMatrix(3)
@test @insrc(sum(m)) == 9
```
