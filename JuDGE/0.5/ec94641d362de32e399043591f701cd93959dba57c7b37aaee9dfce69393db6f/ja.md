```
enforced(model, variable, args...)
```

サブプロブレム `model` 内で強制変数 `variable` を定義します。すべてのサブプロブレムは同じセットの強制変数を持つ必要があることに注意してください。これらの変数は拡張変数またはシャットダウン変数として使用できますが、マスタープロブレムの制約が等式であるため、マスタープロブレムを解く際の柔軟性が少なく、収束が難しくなります。

### 必須引数

`model` は、拡張変数を追加する JuDGE サブプロブレムです。

`variable` は作成される変数の名前で、デフォルトでは連続的です。変数のセットを定義する場合は JuMP 構文に従います。

### オプション引数

このマクロには、`@variable` マクロと同様に、Con、Bin、または Int に設定できる第三の名前のない引数があります。

`lag` は、拡張が決定されてから利用可能になるまでのシナリオ内のノードの数です。

`duration` は、拡張が利用可能なシナリオ内の連続したノードの数です。

`lb` は、マスタープロブレムにおけるこの変数の下限（通常は省略されます）です。

`ub` は、マスタープロブレムにおけるこの変数の上限（通常は省略されます）です。

`penalty` は、将来の機能のためのプレースホルダーであり、コストを伴ってマスター/サブプロブレムの等式制約の違反を許可する可能性があります。

### 例

```
@expansion(model, forced[1:5], Bin) #ラグなしで無制限の寿命を持つ5つのバイナリ変数の配列を定義します
@expansion(model, forced[1:5,1:2]>=0, lag=1) #ラグ1で無制限の期間を持つ10の連続変数の行列を定義します
@expansion(model, 0<=forced<=10, Int, duration=2) #ラグ0で期間2の単一の整数変数を定義します
```
