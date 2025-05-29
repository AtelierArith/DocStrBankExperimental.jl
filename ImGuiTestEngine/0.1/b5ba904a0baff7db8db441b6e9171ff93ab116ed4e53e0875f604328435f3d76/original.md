```julia
primitive type TestRunFlags <: Enum{Int32} 32
```

Wrapper for the upstream `ImGuiTestRunFlags` enum. Possible values:

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
