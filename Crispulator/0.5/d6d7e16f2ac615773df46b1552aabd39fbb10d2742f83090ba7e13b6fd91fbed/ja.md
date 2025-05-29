```julia
struct CRISPRn <: Crispulator.Cas9Behavior
```

CRISPR KOの挙動は、sgRNAによって誘導されるDNA損傷修復が確率的であるため、より複雑です。特定の遺伝子座での修復イベントの2/3がフレームシフトを引き起こすと仮定し、スクリーニングは二倍体細胞で行われるとします。ほとんどのsgRNAに対するCRISPRnスクリーニングで、バイアレルのフレームシフト変異のみが表現型を引き起こすという仮定は、フレーム内欠失が主に強い表現型を示さないという経験的な発見によって支持されています。ただし、保存された残基やドメインをコードする領域で発生する場合を除きます[^2]

[^2]: Horlbeck MA, Gilbert LA, Villalta JE, Adamson B, Pak RA, Chen Y, Fields AP, Park CY, Corn JE, Kampmann M, Weissman JS: Compact and highly active next- generation libraries for CRISPR-mediated gene repression and activation. *Elife* 2016, 5.
