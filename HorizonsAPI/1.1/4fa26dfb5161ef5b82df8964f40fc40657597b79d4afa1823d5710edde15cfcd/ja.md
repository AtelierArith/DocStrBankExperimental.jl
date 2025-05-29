```julia
fetch_spk(
    COMMAND;
    file,
    EMAIL_ADDR,
    START_TIME,
    STOP_TIME,
    format
)

```

指定された `COMMAND` に対して、`EPHEM_TYPE="SPK"` 形式で惑星のエフェメリスを取得します。
