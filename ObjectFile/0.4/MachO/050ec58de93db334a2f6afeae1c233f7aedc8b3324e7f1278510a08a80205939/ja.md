```
MachOLoadCmd(oh::MachOHeader, CT::Type{MachOLoadDylibCmd}, header)
MachOLoadCmd(oh::MachOHeader, CT::Type{MachOIdDylibCmd}, header)
```

MachOファイルから`MachOLoadDylibCmd`をアンパックし、関連する名前文字列を即座に読み込むための手動オーバーライド。詳細は`MachODylibStub`を参照してください。
