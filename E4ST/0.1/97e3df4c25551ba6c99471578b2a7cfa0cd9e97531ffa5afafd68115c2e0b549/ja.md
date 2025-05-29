```
abstract type Iterable
```

時には、非常に似た入力セットでE4STを連続して実行し、実行間で入力の小さな部分を変更することが望ましい場合があります。そのために、このカスタムインターフェースがあります！

`Iterable`は、[`run_e4st`](@ref)が複数の最適化をどのように反復するかを表します。この構造は、次のようなさまざまな目的に使用できます。

  * 年のシーケンスを実行する
  * ある負荷基準を満たすための天然ガスの最適価格を見つけるために反復する。
  * キャパシティ/リタイアメントの最初のシミュレーションを実行し、その後、より高い時間的解像度で発電を見つけるために次のシミュレーションを実行する。

## Iterableをconfigに追加する

  * `Modification`をconfigファイルに追加するのと同じ方法で、`Iterable`をconfigに追加します。すなわち：

```yaml
# config.ymlの内部
iter:
  type: MyIterType
  myfield: myval
```

## インターフェース

  * [`init!(iter::Iterable, config)`](@ref) - （オプション）`config`で`iter`を初期化し、変更を加えます。
  * [`issequential(iter)`](@ref) - （オプション）イテレータが時間を順次進めるかどうかを返します。デフォルトはtrueで、configを別のシミュレーションに再利用できるようにします。
  * [`should_iterate(iter, config, data)`](@ref) - シミュレーションが別の反復のために続行すべきかどうかを返します。
  * [`iterate!(iter, config, data)`](@ref) - 反復間の構造に対して変更を加えます。
  * [`should_reread_data(iter)`](@ref) - 反復時にデータを再読み込みすべきかどうかを返します。
  * [`fieldnames_for_yaml(::Type{<:Iterable})`](@ref) - （オプション）[`save_config`](@ref)でyamlファイルに印刷するフィールド名を返します。
