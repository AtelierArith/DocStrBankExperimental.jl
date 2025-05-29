```
assume_role(role; kwargs...) -> Function
```

IAM `role` を遅延プリンシパルエンティティを介して引き受ける関数を作成します。すなわち、`principal -> assume_role(principal, role; kwargs...)` に相当する関数です。[ロールチェイニング](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_terms-and-concepts.html#iam-term-role-chaining) に便利です。

# 例

"role-a" を引き受け、その後 "role-b" を引き受ける:

```julia
AWSConfig() |> assume_role("role-a") |> assume_role("role-b")
```
