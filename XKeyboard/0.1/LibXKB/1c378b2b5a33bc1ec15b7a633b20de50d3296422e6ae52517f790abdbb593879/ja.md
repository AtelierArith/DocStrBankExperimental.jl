```
xkb_state_update_key(state, key, direction)
```

押されたり解放されたりしている特定のキーを反映するためにキーボードの状態を更新します。

このエントリポイントは、キーボードの状態を明示的に追跡するプログラム（evdevクライアントのような）向けに設計されています。状態がマスタープロセス（Waylandコンポジタのような）によって[`xkb_state_serialize_mods`](@ref)()のような関数を使用してシリアライズされる場合は、代わりに[`xkb_state_update_mask`](@ref)()を使用するべきです。これらの2つの関数は一般的に一緒に使用されるべきではありません。

この関数への一連の呼び出しは一貫している必要があります。つまり、キーに対してXKB*KEY*DOWNでの呼び出しはXKB*KEY*UPで一致する必要があります。キーが2回押された場合は、2回解放されるべきです。そうでない場合（例えば、入力イベントを見逃した場合）、"スタックした修飾キー"のような状況が発生する可能性があります。

この関数は、キーイベントを処理する際に[`xkb_state_key_get_syms`](@ref)()（または[`xkb_state_key_get_one_sym`](@ref)）と一緒に使用されることがよくあります。この場合、キーを更新する前にキーシンボルを取得することを好むべきです。そうすることで、キーイベントに報告されるキーシンボルがそのイベント自体に影響されないようになります。これが従来の動作です。

xkb_state

### 戻り値

更新の結果として変更された状態コンポーネントのマスク。状態に何も変更がない場合は、0を返します。

### 参照

[`xkb_state_update_mask`](@ref)()
