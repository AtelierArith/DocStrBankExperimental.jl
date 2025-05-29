```
xkb_state_serialize_mods(state, components)
```

修飾子用の[`xkb_state_update_mask`](@ref)の対応する関数で、シリアル化のサーバー側で使用されます。

この関数は通常のクライアントでは使用しないでください。代わりにxkb*state*mod***is_active APIを使用してください。

xkb_state

### パラメータ

  * `state`: キーボードの状態。
  * `components`: シリアル化する修飾子状態コンポーネントのマスク。XKB*STATE*MODS**以外の状態コンポーネントは無視されます。XKB*STATE*MODS*EFFECTIVEが含まれている場合、他のすべての状態コンポーネントは無視されます。

### 戻り値

与えられた修飾子状態のコンポーネントを表す[`xkb_mod_mask_t`](@ref)。
