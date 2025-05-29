```
refvalue(A, x)
```

元の配列 `A` と、`refarray(A)` から取得した "ref value" `x` に対して、適切な元の値を返します。`refvalue(A, refarray(A)[I...])` は `A[I...]` と等しくなければなりません。

デフォルトでは、`refvalue(A, x)` は `x` を返します（`refarray(A)` がデフォルトで `A` を返すため）。これにより、"ref values" に対して操作を行った後に元の配列要素を復元することができます。

この汎用関数は DataAPI.jl 自体によって所有されており、デフォルト定義の唯一の提供者です。
