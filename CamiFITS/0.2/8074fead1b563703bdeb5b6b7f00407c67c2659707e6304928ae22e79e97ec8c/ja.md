```
fits_keyword(keyword::String [; msg=true])
fits_keyword([; hdutype="all" [, msg=true]])
```

[FITS標準](https://fits.gsfc.nasa.gov/fits_standard.html)の*予約語*の説明：

(blanks), ALL, AUTHOR, BITPIX, BLANK, BLOCKED, BSCALE, BUNIT, BZERO, CDELTn,  COMMENT, CROTAn, CRPIXn, CRVALn, CTYPEn, DATAMAX, DATAMIN, DATE, DATE-OBS, END, EPOCH, EQUINOX, EXTEND, EXTLEVEL, EXTNAME, EXTVER, GCOUNT, GROUPS, HISTORY, INSTRUME, NAXIS, NAXISn, OBJECT, OBSERVER, ORIGIN, PCOUNT, PSCALn, PTYPEn, PZEROn, REFERENC, SIMPLE, TBCOLn, TDIMn, TDISPn, TELESCOP, TFIELDS, TFORMn, THEAP, TNULLn, TSCALn, TTYPEn, TUNITn, TZEROn, XTENSION,

ここで `n = 1,...,nmax` はキーワードに指定されたものです。キーワード "ALL" を使用して、キーワードの説明の完全なリストをダンプします。

説明は、[FITS標準 - バージョン4.0](https://fits.gsfc.nasa.gov/fits_standard.html)の付録Cに基づいており、*標準の一部ではなく、便利な参照のために含まれています*。

```
julia> fits_keyword("naxisn");
KEYWORD:    NAXISn
REFERENCE:  FITS Standard - version 4.0 - Appendix C
CLASS:      general
STATUS:     mandatory
HDU:        primary, groups, extension, array, image, ASCII-table, bintable,
VALUE:      integer
RANGE:      [0:]
COMMENT:    size of the axis
DEFINITION: The value field of this indexed keyword shall contain a non-negative integer,  
representing the number of elements along axis n of a data array.
The NAXISn must be present for all values n = 1,...,NAXIS, and for no other values of n.   
A value of zero for any of the NAXISn signifies that no data follow the header in the HDU. 
If NAXIS is equal to 0, there should not be any NAXISn keywords.

julia> fits_keyword()
FITS defined keywords:
(blanks) AUTHOR   BITPIX   BLANK    BLOCKED  BSCALE   BUNIT    BZERO    
CDELTn   COMMENT  CROTAn   CRPIXn   CRVALn   CTYPEn   DATAMAX  DATAMIN  
DATE     DATE-OBS END      EPOCH    EQUINOX  EXTEND   EXTLEVEL EXTNAME  
EXTVER   GCOUNT   GROUPS   HISTORY  INSTRUME NAXIS    NAXISn   OBJECT   
OBSERVER ORIGIN   PCOUNT   PSCALn   PTYPEn   PZEROn   REFERENC SIMPLE   
TBCOLn   TDIMn    TDISPn   TELESCOP TFIELDS  TFORMn   THEAP    TNULLn   
TSCALn   TTYPEn   TUNITn   TZEROn   XTENSION

HDU options: 'primary', 'extension', 'array', 'image', 'ASCII-table', 'bintable'

reference: FITS Standard - version 4.0 - Appendix C
```
