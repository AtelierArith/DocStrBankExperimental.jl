```
@isinsrc f([x, y,...])
```

式に対して呼び出されるメソッドが、テストが実行されているモジュールのソースディレクトリ（"src"）にある場合は、trueを返します。

`@isinsrc`はモジュールの"test"ディレクトリ内から呼び出されることを意図しています。srcディレクトリは"test/../src"を介して見つけられます。

### 例

`sum`のメソッドが`MyPackage`に定義されていることを確認します。

```julia
using MyPackage
using MethodInSrc
using Test

m = MyPackage.AMatrix(3)
@test @isinsrc sum(m)
```
