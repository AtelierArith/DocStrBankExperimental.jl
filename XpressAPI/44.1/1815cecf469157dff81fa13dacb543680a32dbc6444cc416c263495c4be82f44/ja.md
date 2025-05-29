```
XPRSaddcbgapnotify(prob, cb, priority)
```

# 引数

  * `cbprob`: 現在の問題。
  * `relgapnotifytarget`: このコールバックの後にMIPRELGAPNOTIFY制御が設定される値。新しい通知ターゲットを設定するためにコールバック内で変更することができます。
  * `absgapnotifytarget`: このコールバックの後にMIPABSGAPNOTIFY制御が設定される値。新しい通知ターゲットを設定するためにコールバック内で変更することができます。
  * `absgapnotifyobjtarget`: このコールバックの後にMIPABSGAPNOTIFYOBJ制御が設定される値。新しい通知ターゲットを設定するためにコールバック内で変更することができます。
  * `absgapnotifyboundtarget`: このコールバックの後にMIPABSGAPNOTIFYBOUND制御が設定される値。新しい通知ターゲットを設定するためにコールバック内で変更することができます。

`cb`はこのシグネチャで呼び出されます：

```
cb(cbprob, relgapnotifytarget, absgapnotifytarget, absgapnotifyobjtarget, absgapnotifyboundtarget)::relgapnotifytarget, absgapnotifytarget, absgapnotifyobjtarget, absgapnotifyboundtarget
```
