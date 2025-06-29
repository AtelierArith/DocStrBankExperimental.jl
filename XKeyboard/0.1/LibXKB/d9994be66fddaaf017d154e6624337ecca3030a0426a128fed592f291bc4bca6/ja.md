```
xkb_keysym_from_name(name, flags)
```

名前から keysym を取得します。

XKB*KEYSYM*CASE*INSENSITIVE フラグを使用し、2 つの keysym 名が大文字と小文字の違いのみで異なる場合、低いケースの keysym が返されます。たとえば、KEY*a と KEY*A の場合、この関数は大文字と小文字を区別しない検索のために KEY*a を返します。この機能が必要な場合は、最初にこのフラグなしでこの関数を呼び出すことをお勧めします。そして、それが失敗した場合にのみ、このフラグを使用して試み、ユーザーに名前を誤って入力した可能性があることを警告し、間違った結果が得られるかもしれないことを伝えます。

ケースフォールディングは C ロケールに従って行われます。現在のロケールは考慮されません。

### パラメータ

  * `name`: keysym の名前。[`xkb_keysym_get_name`](@ref)() の備考を参照してください。この関数は、その関数によって返された任意の名前を受け入れます。
  * `flags`: 検索方法を制御するフラグのセット。無効なフラグが渡された場合、これは [`XKB_KEY_NoSymbol`](@ref) で失敗します。

### 戻り値

keysym。名前が無効な場合、[`XKB_KEY_NoSymbol`](@ref) を返します。

### 参照

[`xkb_keysym_t`](@ref) ```
