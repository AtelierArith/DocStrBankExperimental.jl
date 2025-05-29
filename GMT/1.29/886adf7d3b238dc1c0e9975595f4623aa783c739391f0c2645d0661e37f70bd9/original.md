```
image_cpt!(img::GMTimage, cpt::GMTcpt, clear=false)
```

or

```
image_cpt!(img::GMTimage, cpt::String, clear=false)
```

Add (or replace) a colormap to a GMTimage object from the colors in the cpt. This should have effect only if IMG is indexed. Use `image_cpt!(img, clear=true)` to remove a previously existant `colormap` field in IMG
