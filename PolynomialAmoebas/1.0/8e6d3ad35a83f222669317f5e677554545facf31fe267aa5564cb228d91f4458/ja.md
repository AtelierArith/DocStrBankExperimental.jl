```
MembershipTestResult{T, N}
```

**フィールド**

  * `successfull::Bool`
  * `tries::Int` ニュートン法が開始された回数
  * `converged_iterations::Int` 成功した反復に必要な反復回数。テストが成功しなかった場合、`imax` は最大反復回数です。
  * `startvalue::SVector{N, T}` 成功した反復の開始値。それ以外はランダム値です。
  * `solution::SVector{N, T}` 成功した反復の解の値。それ以外はランダム値です。
