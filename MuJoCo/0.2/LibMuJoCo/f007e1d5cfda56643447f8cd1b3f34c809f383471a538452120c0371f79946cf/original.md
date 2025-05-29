```
mjrContext
```

# Fields

  * **`lineWidth`**: line width for wireframe rendering
  * **`shadowClip`**: clipping radius for directional lights
  * **`shadowScale`**: fraction of light cutoff for spot lights
  * **`fogStart`**: fog start = stat.extent * vis.map.fogstart
  * **`fogEnd`**: fog end = stat.extent * vis.map.fogend
  * **`fogRGBA`**: fog rgba
  * **`shadowSize`**: size of shadow map texture
  * **`offWidth`**: width of offscreen buffer
  * **`offHeight`**: height of offscreen buffer
  * **`offSamples`**: number of offscreen buffer multisamples
  * **`fontScale`**: font scale
  * **`auxWidth`**: auxiliary buffer width
  * **`auxHeight`**: auxiliary buffer height
  * **`auxSamples`**: auxiliary buffer multisamples
  * **`offFBO`**: offscreen framebuffer object
  * **`offFBO_r`**: offscreen framebuffer for resolving multisamples
  * **`offColor`**: offscreen color buffer
  * **`offColor_r`**: offscreen color buffer for resolving multisamples
  * **`offDepthStencil`**: offscreen depth and stencil buffer
  * **`offDepthStencil_r`**: offscreen depth and stencil buffer for resolving multisamples
  * **`shadowFBO`**: shadow map framebuffer object
  * **`shadowTex`**: shadow map texture
  * **`auxFBO`**: auxiliary framebuffer object
  * **`auxFBO_r`**: auxiliary framebuffer object for resolving
  * **`auxColor`**: auxiliary color buffer
  * **`auxColor_r`**: auxiliary color buffer for resolving
  * **`ntexture`**: number of allocated textures
  * **`textureType`**: type of texture (mjtTexture) (ntexture)
  * **`texture`**: texture names
  * **`basePlane`**: all planes from model
  * **`baseMesh`**: all meshes from model
  * **`baseHField`**: all hfields from model
  * **`baseBuiltin`**: all buildin geoms, with quality from model
  * **`baseFontNormal`**: normal font
  * **`baseFontShadow`**: shadow font
  * **`baseFontBig`**: big font
  * **`rangePlane`**: all planes from model
  * **`rangeMesh`**: all meshes from model
  * **`rangeHField`**: all hfields from model
  * **`rangeBuiltin`**: all builtin geoms, with quality from model
  * **`rangeFont`**: all characters in font
  * **`nskin`**: number of skins
  * **`skinvertVBO`**: skin vertex position VBOs (nskin)
  * **`skinnormalVBO`**: skin vertex normal VBOs (nskin)
  * **`skintexcoordVBO`**: skin vertex texture coordinate VBOs (nskin)
  * **`skinfaceVBO`**: skin face index VBOs (nskin)
  * **`charWidth`**: character widths: normal and shadow
  * **`charWidthBig`**: chacarter widths: big
  * **`charHeight`**: character heights: normal and shadow
  * **`charHeightBig`**: character heights: big
  * **`glInitialized`**: is OpenGL initialized
  * **`windowAvailable`**: is default/window framebuffer available
  * **`windowSamples`**: number of samples for default/window framebuffer
  * **`windowStereo`**: is stereo available for default/window framebuffer
  * **`windowDoublebuffer`**: is default/window framebuffer double buffered
  * **`currentBuffer`**: currently active framebuffer: mjFB*WINDOW or mjFB*OFFSCREEN
  * **`readPixelFormat`**: default color pixel format for mjr_readPixels
  * **`readDepthMap`**: depth mapping: mjDEPTH*ZERONEAR or mjDEPTH*ZEROFAR
