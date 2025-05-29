```
HallOfFame{T<:DATA_TYPE,L<:LOSS_TYPE}
```

全時代で見られた最高のメンバーのリストは `.members` にあり、`.members[c]` は複雑さ c で見られた最高のメンバーです。実際に設定されたメンバーのみを含めるには、`.members[exists]` を実行できます。

# フィールド

  * `members::Array{PopMember{T,L},1}`: 全時代で見られた最高のメンバーのリスト。これらは複雑さによって順序付けられており、`.members[1]` は複雑さ 1 のメンバーです。
  * `exists::Array{Bool,1}`: 指定された複雑さのメンバーが設定されているかどうか。
