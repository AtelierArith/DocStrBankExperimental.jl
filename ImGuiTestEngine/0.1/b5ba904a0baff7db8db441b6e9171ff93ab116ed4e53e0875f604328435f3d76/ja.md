```julia
primitive type TestRunFlags <: Enum{Int32} 32
```

上流の `ImGuiTestRunFlags` 列挙型のラッパー。可能な値：

  * `TestRunFlags_None`
  * `TestRunFlags_GuiFuncDisable`
  * `TestRunFlags_GuiFuncOnly`
  * `TestRunFlags_NoSuccessMsg`
  * `TestRunFlags_EnableRawInputs`
  * `TestRunFlags_RunFromGui`
  * `TestRunFlags_RunFromCommandLine`
  * `TestRunFlags_NoError`
  * `TestRunFlags_ShareVars`
  * `TestRunFlags_ShareTestContext`
