```
xkb_state_mod_name_is_active(state, name, type)
```

指定されたキーボード状態で修飾子が名前によってアクティブかどうかをテストします。

xkb_state

### 戻り値

修飾子がアクティブな場合は1、そうでない場合は0を返します。修飾子名がキーマップに存在しない場合は-1を返します。
