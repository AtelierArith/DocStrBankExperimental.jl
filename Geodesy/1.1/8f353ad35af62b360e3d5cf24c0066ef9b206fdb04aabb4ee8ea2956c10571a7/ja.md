```
WebMercatorfromLLA(datum=wgs84)
```

LLAからWeb Mercator / Pseudo Mercatorに変換します。これは、楕円体の長半径のスケーリングファクターを使用するprojの規約に従っています。https://proj.org/operations/projections/webmerc.html

!!! warning
    ウェブマッピングアプリケーションでは、この投影法は実装の簡便さから広く使用されていますが、この簡便さは数学的特性の悪さをもたらします：赤道から離れると角度を保持しません。測定が重要な場合は、可能であれば他の投影法を優先すべきです。詳細な議論については、https://earth-info.nga.mil/GandG/wgs84/web*mercator/(U)%20NGA*SIG*0011*1.0.0_WEBMERC.pdfを参照してください。

