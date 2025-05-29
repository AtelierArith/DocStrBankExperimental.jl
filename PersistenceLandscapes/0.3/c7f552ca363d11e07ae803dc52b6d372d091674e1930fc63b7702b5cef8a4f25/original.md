Split the lifespan of barcodes into 'numberOfBins' bins and refactor bars such that their birth and death is one of the bins.

This works as follows:

  * create barcode with earliest birth and latests death in 'pers_barcode'
  * split the range into 'numberOfBins' bins
  * get unit barcode length, that is (latest death - earliest birth)/numberOfBins
  * for each barcode from 'pers_barcode':

      * get index of the bin where is the barcode born
      * get index of the bin where the barcode dies
      * create a new barcode with birth equal to (unit length) * (birth index) and   death equal to (unit length) * (death index)
