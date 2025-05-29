```
MachOIdDylibCmd
```

MachO dylibs は ELF 共有ライブラリの SONAME に類似した「アイデンティティ」を持っています。この Load Command はリンカーにこの特定の共有ライブラリのアイデンティティについて知らせます。このオブジェクトの API は `MachOLoadDylibCmd` オブジェクトのそれと同一であり、内面的には同じであるため、データの背後にある意味が変わるだけであり、このオブジェクトはほぼ `MachOLoadDylibCmd` の型エイリアスです。
