```
mjrContext
```

# フィールド

  * **`lineWidth`**: ワイヤーフレームレンダリングの線の幅
  * **`shadowClip`**: 指向性光源のクリッピング半径
  * **`shadowScale`**: スポットライトの光カットオフの割合
  * **`fogStart`**: 霧の開始 = stat.extent * vis.map.fogstart
  * **`fogEnd`**: 霧の終了 = stat.extent * vis.map.fogend
  * **`fogRGBA`**: 霧のrgba
  * **`shadowSize`**: シャドウマップテクスチャのサイズ
  * **`offWidth`**: オフスクリーンバッファの幅
  * **`offHeight`**: オフスクリーンバッファの高さ
  * **`offSamples`**: オフスクリーンバッファのマルチサンプル数
  * **`fontScale`**: フォントスケール
  * **`auxWidth`**: 補助バッファの幅
  * **`auxHeight`**: 補助バッファの高さ
  * **`auxSamples`**: 補助バッファのマルチサンプル数
  * **`offFBO`**: オフスクリーンフレームバッファオブジェクト
  * **`offFBO_r`**: マルチサンプルを解決するためのオフスクリーンフレームバッファ
  * **`offColor`**: オフスクリーンカラー バッファ
  * **`offColor_r`**: マルチサンプルを解決するためのオフスクリーンカラー バッファ
  * **`offDepthStencil`**: オフスクリーン深度およびステンシルバッファ
  * **`offDepthStencil_r`**: マルチサンプルを解決するためのオフスクリーン深度およびステンシルバッファ
  * **`shadowFBO`**: シャドウマップフレームバッファオブジェクト
  * **`shadowTex`**: シャドウマップテクスチャ
  * **`auxFBO`**: 補助フレームバッファオブジェクト
  * **`auxFBO_r`**: 解決のための補助フレームバッファオブジェクト
  * **`auxColor`**: 補助カラー バッファ
  * **`auxColor_r`**: 解決のための補助カラー バッファ
  * **`ntexture`**: 割り当てられたテクスチャの数
  * **`textureType`**: テクスチャの種類 (mjtTexture) (ntexture)
  * **`texture`**: テクスチャ名
  * **`basePlane`**: モデルからのすべての平面
  * **`baseMesh`**: モデルからのすべてのメッシュ
  * **`baseHField`**: モデルからのすべてのhfield
  * **`baseBuiltin`**: モデルからの品質を持つすべてのビルトインジオメトリ
  * **`baseFontNormal`**: 通常のフォント
  * **`baseFontShadow`**: シャドウフォント
  * **`baseFontBig`**: 大きなフォント
  * **`rangePlane`**: モデルからのすべての平面
  * **`rangeMesh`**: モデルからのすべてのメッシュ
  * **`rangeHField`**: モデルからのすべてのhfield
  * **`rangeBuiltin`**: モデルからの品質を持つすべてのビルトインジオメトリ
  * **`rangeFont`**: フォント内のすべての文字
  * **`nskin`**: スキンの数
  * **`skinvertVBO`**: スキン頂点位置VBO (nskin)
  * **`skinnormalVBO`**: スキン頂点法線VBO (nskin)
  * **`skintexcoordVBO`**: スキン頂点テクスチャ座標VBO (nskin)
  * **`skinfaceVBO`**: スキン面インデックスVBO (nskin)
  * **`charWidth`**: 文字の幅: 通常およびシャドウ
  * **`charWidthBig`**: 文字の幅: 大きい
  * **`charHeight`**: 文字の高さ: 通常およびシャドウ
  * **`charHeightBig`**: 文字の高さ: 大きい
  * **`glInitialized`**: OpenGLは初期化されていますか
  * **`windowAvailable`**: デフォルト/ウィンドウフレームバッファは利用可能ですか
  * **`windowSamples`**: デフォルト/ウィンドウフレームバッファのサンプル数
  * **`windowStereo`**: デフォルト/ウィンドウフレームバッファにステレオは利用可能ですか
  * **`windowDoublebuffer`**: デフォルト/ウィンドウフレームバッファはダブルバッファリングされていますか
  * **`currentBuffer`**: 現在アクティブなフレームバッファ: mjFB*WINDOW または mjFB*OFFSCREEN
  * **`readPixelFormat`**: mjr_readPixelsのデフォルトカラー ピクセル形式
  * **`readDepthMap`**: 深度マッピング: mjDEPTH*ZERONEAR または mjDEPTH*ZEROFAR
