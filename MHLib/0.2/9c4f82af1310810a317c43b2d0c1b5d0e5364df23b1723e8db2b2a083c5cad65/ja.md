```
parse_settings!(settings_cfgs::Vector{ArgParseSettings}=mhlib_settings_cfgs; args=ARGS)
```

引数を解析し、グローバルな `settings` をそれに応じて初期化します。

また、`settings[:seed] != 0` の場合は、ランダムに乱数生成器を初期化します。`settings_cfgs` には、このモジュールの基本的な `settings_cfg` に加えて使用する個々のモジュールの ArgParseSettings のリストを提供する必要があります。`MHLib.mhlib_settings_cfgs` を使用して、すべてのモジュールのすべての設定を含めることができます。
