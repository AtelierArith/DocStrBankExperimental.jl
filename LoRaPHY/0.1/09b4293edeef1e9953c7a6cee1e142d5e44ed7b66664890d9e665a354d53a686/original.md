Generate LoRa symbols  sig,bitSeq,bitEnc,bitInter = loraEncode(N,SF,BW,Fs,inverse)

# Input

  * N: Number of block to transmit, a block correspond to SF LoRa symbols
  * SF: Spreading factor of the CSS modulation
  * BW: Bandwidth used for transmission
  * Fs: sampling frequency
  * inverse: 0 to send upchirp, 1 for downchirp

# Output

  * sig : Baseband  signal emitted from the transmitter (complex form)
  * bitSeq : randomly generated binary data (Payload message)
  * bitEnc : Binary sequence after Hamming encoding
  * bitInterl : Binary sequence after interleaving

Dispatch method :  sig,bitSeq,bitEnc,bitInter = lora_encode(bitSeq,SF,BW,Fs,inverse) 
- Uses a payload message bitSeq (must be of size N x SF x 4)
