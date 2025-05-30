```
supervise(sv, child=self(); cb=nothing, restart::Symbol=:transient)
```

スーパーバイザー `sv` に指定された `child` アクターを監視するよう指示します。

# 引数

  * `sv`: スーパーバイザーのリンクまたは登録名、
  * `child`: 監視するアクターのリンクまたは登録名。

# キーワード引数

  * `cb=nothing`: コールバック（呼び出し可能なオブジェクト）、前のアクターの動作を引数として受け取り、新しいアクターへの [`Link`](@ref) を返さなければなりません。`nothing` の場合、アクターはその [`init!`](@ref) コールバックまたは前の動作で再起動されます。
  * `restart::Symbol=:transient`: [再起動オプション](@ref restart)、`:permanent`、`:temporary`、`:transient` のいずれか、
