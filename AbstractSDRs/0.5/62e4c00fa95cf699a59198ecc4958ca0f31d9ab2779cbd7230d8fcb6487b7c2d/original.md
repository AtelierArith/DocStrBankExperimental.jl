Scan interface and returns the founded SDR 

# –- Syntax

sdr = scan()  sdr = scan(backend;key...)

# Input parameter

If the function is called without parameters il will search for all available backends such as UHDBindings and AdalmPluto. Otherwise the search will be limited to the desired backend  The optionnal arguments are the one supported by UHDBindings and AdalmPluto. See `uhd_find_devices()` in UHDBindings and `scan` function in AdalmPluto 

# Keywords

  * args : String used in UHD backend to specify USRP IP address. Example: scan(:uhd;args="addr=192.168.10.16")
  * backend : Sring used in Pluto backend to specify the interface used ("local", "xml", "ip", "usb")
