```
cpuarchitecture()
```

この関数は、`cpuid`命令を呼び出すことでCPUマイクロアーキテクチャを推測しようとします。 現在のところ、次の表に従ってIntel CPUのみがサポートされています。他は`:Unknown`として識別されます。

Intelの最適化リファレンスマニュアルの表C-1：

| Family_Model                   | Microarchitecture   |
|:------------------------------ |:------------------- |
| 06*4EH, 06*5EH                 | Skylake             |
| 06*3DH, 06*47H, 06_56H         | Broadwell           |
| 06*3CH, 06*45H, 06*46H, 06*3FH | Haswell             |
| 06*3AH, 06*3EH                 | Ivy Bridge          |
| 06*2AH, 06*2DH                 | Sandy Bridge        |
| 06*25H, 06*2CH, 06_2FH         | Westmere            |
| 06*1AH, 06*1EH, 06*1FH, 06*2EH | Nehalem             |
| 06*17H, 06*1DH                 | Enhanced Intel Core |
| 06_0FH                         | Intel Core          |
