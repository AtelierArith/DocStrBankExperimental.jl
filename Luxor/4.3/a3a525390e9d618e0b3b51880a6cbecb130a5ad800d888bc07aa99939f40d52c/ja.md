```
sector(centerpoint::Point, innerradius, outerradius,
        startangle, endangle, cornerradius;
       action:none)
```

中心点 `centerpoint` を中心に、丸みを帯びた角を持つ環状セクターを作成し、現在のパスに追加します。基本的には曲がったソーセージの形です。

TODO: 現在のところ、結果は100%正確ではありません。曲線が接続する部分に小さな不連続性があります。

TODO - ブール値よりも役立つものを返す

コーナー半径は、オーバーシュートを防ぐために必要に応じて供給された値から減少します。
