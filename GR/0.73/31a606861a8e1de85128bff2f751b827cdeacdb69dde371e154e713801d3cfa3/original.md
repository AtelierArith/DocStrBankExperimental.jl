```
init(always::Bool = false)

Initialize GR's environmental variables before plotting and ensure that the
binary shared libraries are loaded. Initialization usually only needs to be
done once, but reinitialized may be required when settings change.

The `always` argument is true if initialization should be forced in the
current and subsequent calls. It is `false` by default so that
initialization only is done once.

# Extended Help

Environmental variables which influence `init`:
GRDISPLAY - if "js" or "pluto", javascript support is initialized
GKS_NO_GUI - no initialization is done
GKS_IGNORE_ENCODING - Force use of UTF-8 for font encoding, ignore GKS_ENCODING

Environmental variables set by `init`:
GKS_FONTPATH - path to GR fonts, often the same as GRDIR
GKS_USE_CAIRO_PNG
GKSwstype - Graphics workstation type, see help for `openws`
GKS_QT - Command to start QT backend via gksqt executable
GKS_ENCODING - Sets the text encoding (e.g. Latin1 or UTF-8)
```
