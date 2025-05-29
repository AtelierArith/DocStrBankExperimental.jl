```
DomainRestrictions{P <: GeneralVariableRef}
```

特定の無限パラメータをその全体ドメインに対するサブドメインに制約する区間ドメインを格納するための `DataType` です。これは [`DomainRestrictedConstraint`](@ref) のサブドメインを定義するために使用されます。GeneralVariableRef は無限パラメータに関連している必要があります。

コンストラクタの構文は次のとおりです。

```julia
DomainRestrictions(restrictions...)
```

ここで、`restrictions` の各引数は次のいずれかの形式です：

  * `pref => value`
  * `pref => [lb, ub]`
  * `pref => IntervalDomain(lb, ub)`
  * `prefs => value`
  * `prefs => [lb, ub]`
  * `prefs => IntervalDomain(lb, ub)`。

`pref` と `prefs` は無限パラメータに対応している必要があります。

**フィールド**

  * `intervals::Dict{GeneralVariableRef, IntervalDomain}`: 無限パラメータに対する区間境界の辞書。
