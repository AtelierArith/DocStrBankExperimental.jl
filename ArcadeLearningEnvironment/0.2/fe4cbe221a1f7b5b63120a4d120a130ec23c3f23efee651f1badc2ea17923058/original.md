```
loadROM(ale_instance::ALEPtr, rom_file::String)
```

Loads the binary of passed. `rom_file` can either be the absolute path to the binary, or the name of the ROM that is present in the "deps/roms" directory. Access this list using `getROMList()`.

# Examples

```julia-repl
julia> loadROM(ale, "pong")
Game console created:
  ROM file:  /Users/juliauser/.julia/artifacts/4af00c03a4bcddb3ce20c2d96c3d09527100767/ROMS/pong.bin
  Cart Name: Video Olympics (1978) (Atari)
  Cart MD5:  60e0ea3cbe0913d39803477945e9e5ec
  Display Format:  AUTO-DETECT ==> NTSC
  ROM Size:        2048
  Bankswitch Type: AUTO-DETECT ==> 2K


WARNING: Possibly unsupported ROM: mismatched MD5.
Cartridge_MD5: 60e0ea3cbe0913d39803477945e9e5ec
Cartridge_name: Video Olympics (1978) (Atari)

Running ROM file...
Random seed is 0

julia> loadROM(ale, "/Users/juilauser/Desktop/pewpew/roms/ms_pacman.bin")
Game console created:
  ROM file:  /Users/juilauser/Desktop/pewpew/roms/ms_pacman.bin
  Cart Name: Ms. Pac-Man (1982) (CCE)
  Cart MD5:  9469d18238345d87768e8965f9f4a6b2
  Display Format:  AUTO-DETECT ==> NTSC
  ROM Size:        8192
  Bankswitch Type: AUTO-DETECT ==> F8


WARNING: Possibly unsupported ROM: mismatched MD5.
Cartridge_MD5: 9469d18238345d87768e8965f9f4a6b2
Cartridge_name: Ms. Pac-Man (1982) (CCE)

Running ROM file...
Random seed is 0
```
