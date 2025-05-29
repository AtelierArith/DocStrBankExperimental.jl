```
get_test_env(jw::JuliaWorkspace, uri::URI)
```

与えられた `uri` に属するテスト環境をワークスペース `jw` から取得します。

返すもの

  * 構造体 [`JuliaTestEnv`](@ref) のインスタンス
