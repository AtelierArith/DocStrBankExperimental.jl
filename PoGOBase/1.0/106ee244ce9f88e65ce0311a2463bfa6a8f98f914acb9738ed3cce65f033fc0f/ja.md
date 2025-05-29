```
kmcost(poke::Pokemon, target_level_or_cplimit, candy=0, candyxl=0; add_move=true, as=Species(poke))
```

`poke`を`target_level`までパワーアップするために必要なバディウォーク距離を推定します。`candy`と`candyxl`は、あなたが所有し、パワーアップに使えるキャンディの量です。`target_level_or_cplimit`は、500以上の場合はバトルリーグのCP制限として解釈され、それ以外の場合はターゲットレベルとして解釈されます。3つ目の技を購入する必要がない場合は、`add_move=false`に設定してください。

XLキャンディの場合、距離は確率的であり、バディレベルが上がるにつれてXLキャンディの獲得率が増加し、レベル31で最大になります: https://thesilphroad.com/science/quick-discovery/early-look-buddy-candy-xl-rates。XLキャンディを得るために歩く必要がある場合、計算はできるだけ早くレベル31までパワーアップすることを前提としています（例：通常のキャンディを得ながらパワーアップし、レベル31に達するまで進化や3つ目の技の購入を待つ）。この戦略に従わないと、必要な距離が増加する可能性があります。逆に、すでにレベル31以上の同じ種の別のポケモンを歩かせると、必要な距離が減少する可能性があります。
