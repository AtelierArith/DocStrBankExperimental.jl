```
membershiptest(F::AbstractFiber{T}, w:, options=MembershipTestOptions()) where T
```

点 `w` がファイバー `F` に含まれているかどうかを確認します。このテストは、`options` で提供された設定を使用してニュートン法を使用します。[`MembershipTestResult`](@ref) を返します。
