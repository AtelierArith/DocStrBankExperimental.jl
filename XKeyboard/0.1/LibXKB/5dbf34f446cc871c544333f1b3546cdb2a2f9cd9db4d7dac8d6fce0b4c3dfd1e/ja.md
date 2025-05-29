```
xkb_state_serialize_layout(state, components)
```

レイアウト用の[`xkb_state_update_mask`](@ref)の対応物で、シリアル化のサーバー側で使用されます。

この関数は通常のクライアントでは使用しないでください。代わりにxkb*state*layout***is_active APIを使用してください。

xkb_state

### パラメータ

  * `state`: キーボードの状態。
  * `components`: シリアル化するレイアウト状態コンポーネントのマスク。XKB*STATE*LAYOUT**以外の状態コンポーネントは無視されます。XKB*STATE*LAYOUT*EFFECTIVEが含まれている場合、他のすべての状態コンポーネントは無視されます。

### 戻り値

指定されたレイアウト状態のコンポーネントを表すレイアウトインデックス。
