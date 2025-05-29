```
refpool(A)
```

利用可能な場合は、インデックス可能なオブジェクト `pool` を返します。これは、*元の* 配列 `A` と `refarray(A)` から取得した "ref value" `x` が与えられたときに、`pool[x]` が適切な *元の* 値であることを意味します。そのようなオブジェクトが利用できない場合は `nothing` を返します。

デフォルトでは、`refpool(A)` は `nothing` を返します。

`refpool(A)` が `nothing` でない場合、`refpool(A)[refarray(A)[I...]]` は `A[I...]` と等しく（`isequal` に従って）同じ型でなければならず、`refpool(A)` によって返されるオブジェクトは、`AbstractArray` インターフェースに従って、イテレーションおよびインデクシングインターフェース、ならびに `length`、`eachindex`、`keys`、`values`、`pairs`、`firstindex`、`lastindex`、および `eltype` 関数を実装している必要があります。

この汎用関数は DataAPI.jl 自体に属しており、デフォルトの定義の唯一の提供者です。
