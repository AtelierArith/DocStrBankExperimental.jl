@handlemissings_stub(fun, ...)

[`handlemissings`](@ref)を呼び出す際に、ディスパッチマッチを作成するだけで、まだ欠損値を処理する実装はありません。

  * 引数の型をAnyにデフォルト設定し、デフォルト戦略を提供しない（これを変更するには引数を使用します。）
  * MissingStrategy引数を挿入したメソッドが、ディスパッチ関数に転送します。
  * 欠損値を許可しないeltypeのためのディスパッチメソッドが、MissingStrategyなしで元の関数を呼び出します。

引数：[`handlemissings`](@ref)を参照    

その後、Simpletraitsの`@traitfn`を使用して他のメソッドを自分で定義できます。

```jldoctest; output=false
using SimpleTraits
f1(x::AbstractArray{<:Real}) = "欠損値を受け入れないメソッド"
@handlemissings_stub(
  # 呼び出される元の関数と一致するシグネチャ
  f1(x::AbstractArray{<:Real}) = 0,
  # pos_missing, pos_strategy, type_missing, defaultstrategy
  1,2,AbstractArray{<:Union{Missing,Real}}, PassMissing()
) 
methods(f1) # 新しいメソッドが定義されたことを確認するため
# 新しいメソッドは、特別なケースのために拡張できる新しい関数f1_hmに転送されます
# 引数の順序に注意：ディスパッチ関数では欠損戦略が最初に来ます
@traitfn function f1_hm(ms::PassMissing, x::::IsEltypeSuperOfMissing) 
  "eltypeの欠損値を処理するメソッド"
end
f1([1.0,2.0]) == "欠損値を受け入れないメソッド"
f1([1.0,2.0], PassMissing()) == "欠損値を受け入れないメソッド"
f1([1.0,2.0,missing]) == "eltypeの欠損値を処理するメソッド"
# 出力
true
```
