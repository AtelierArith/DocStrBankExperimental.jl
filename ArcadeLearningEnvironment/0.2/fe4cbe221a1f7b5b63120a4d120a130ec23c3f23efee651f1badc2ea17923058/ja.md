```
loadROM(ale_instance::ALEPtr, rom_file::String)
```

渡されたバイナリを読み込みます。`rom_file`は、バイナリの絶対パスであるか、"deps/roms"ディレクトリに存在するROMの名前であることができます。このリストには`getROMList()`を使用してアクセスします。

# 例

```julia-repl
julia> loadROM(ale, "pong")
ゲームコンソールが作成されました:
  ROMファイル:  /Users/juliauser/.julia/artifacts/4af00c03a4bcddb3ce20c2d96c3d09527100767/ROMS/pong.bin
  カートリッジ名: ビデオオリンピック (1978) (アタリ)
  カートリッジMD5:  60e0ea3cbe0913d39803477945e9e5ec
  表示形式:  自動検出 ==> NTSC
  ROMサイズ:        2048
  バンクスイッチタイプ: 自動検出 ==> 2K


警告: おそらくサポートされていないROM: MD5が不一致です。
カートリッジ_MD5: 60e0ea3cbe0913d39803477945e9e5ec
カートリッジ名: ビデオオリンピック (1978) (アタリ)

ROMファイルを実行中...
ランダムシードは0です

julia> loadROM(ale, "/Users/juilauser/Desktop/pewpew/roms/ms_pacman.bin")
ゲームコンソールが作成されました:
  ROMファイル:  /Users/juliauser/Desktop/pewpew/roms/ms_pacman.bin
  カートリッジ名: Ms. Pac-Man (1982) (CCE)
  カートリッジMD5:  9469d18238345d87768e8965f9f4a6b2
  表示形式:  自動検出 ==> NTSC
  ROMサイズ:        8192
  バンクスイッチタイプ: 自動検出 ==> F8


警告: おそらくサポートされていないROM: MD5が不一致です。
カートリッジ_MD5: 9469d18238345d87768e8965f9f4a6b2
カートリッジ名: Ms. Pac-Man (1982) (CCE)

ROMファイルを実行中...
ランダムシードは0です
```
