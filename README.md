# Web3 para Patos

Curso introdutório de Web3 (aplicações descentralizadas WEB com blockchain) para desenvolvedores curiosos.

## Rascunho de tópicos

Contexto

- História do dinheiro
- Bitcoin
- Ethereum
- Altcoins
- Gerações de blockchains
- Crédito de Carbono
- Algorand - A Blockchain Verde


Exploração

- algoexplorer
- Transações
- Contas
- Transferências
- FTs e NFTs

Mão na massa 1

- Criar carteira e conta
- Senha e Mnemônico
- Endereço
- Transferência 

Conceitos - criptografia

- Encoding
  - Hexadecimal
  - Base64
  - Base32

- Hash

Mão na massa 2

- replit

```go
package main

import (
	"fmt"
  "strings"
  
  "encoding/base32"
  "encoding/base64"
  
  "crypto/md5"
  "crypto/sha1"
  "crypto/sha256"
  "crypto/sha512"
  
  "crypto/ed25519"
  
)

func main() {
  imprimir([]byte("ABCD"), "bytes a partir de string")

  // ABCD
  texto := []byte{65,66,67,68}
  imprimir(texto, "bytes diretos no array")

  // For regular addresses, the address is the base32 encoding 
  // of a 32-byte ed25519 public key and a 4-byte checksum.
  // (If you’re interested, the checksum is the last 4 bytes 
  // of the SHA-512/256 hash of the  public key.)

  
  public_key, private_key, _ := ed25519.GenerateKey(nil)
  imprimir(public_key, "chave pública")
  // QI44NKJ65KRZYGAU7Y77TXQBGJNEJKULDGNJU66NTAHO457X3DZA

  hash_da_public_key := sha512.Sum512_256(public_key) // 32 bytes
  digitosVerificadores := hash_da_public_key[28:] // 4 últimos de 32 -> posições 28, 29, 30 e 31
  imprimir(digitosVerificadores, "DVs")

  imprimir(append(public_key, digitosVerificadores...), "chave pública + DVs")
   // QI44NKJ65KRZYGAU7Y77TXQBGJNEJKULDGNJU66NTAHO457X3DZMMW3VX4
  


  
  
  // assinar texto com PRIVADA
  texto_original := []byte("Essa á a mensagem original")
  imprimir(texto_original, "texto_original")
  texto_assinado := ed25519.Sign(private_key, texto_original)
  imprimir(texto_assinado, "texto_assinado")
  
  // verificar assinatura com PÚBLICA
  posso_confiar := ed25519.Verify(public_key, texto_original, texto_assinado)
  fmt.Printf("\n\nPosso confiar?: %v\n", posso_confiar)

  texto_alterado := []byte("Essa á a mensagem original ") // um espaço no fim
  imprimir(texto_alterado, "texto_alterado")
  posso_confiar = ed25519.Verify(public_key, texto_alterado, texto_assinado)
  fmt.Printf("\n\nPosso confiar?: %v\n", posso_confiar)
  
}



func imprimir(texto []byte, titulo string) {
  fmt.Printf("\n\n-- %s %s\n", titulo, strings.Repeat("-", 80 - len(titulo)))
  
  // representação texto 
  fmt.Printf("\n%s\n", texto)

  // representação em base 2
  // alfabeto: 01
  fmt.Printf("\n%b\n", texto)

  // representação em base 10
  // alfabeto: 0123456789
  fmt.Printf("\n%d\n", texto)

  // representação em base 16
  // alfabeto: 0123456789ABCDEF
  fmt.Printf("\n%x\n", texto)

  // representação em base 32
  // alfabeto: ABCDEFGHIJKLMNOPQRSTUVWXYZ234567
  fmt.Printf("\n%s\n", base32.StdEncoding.EncodeToString(texto))

  // representação em base 64
  // alfabeto: ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789+/
  fmt.Printf("\n%s\n", base64.StdEncoding.EncodeToString(texto))
}

func computarHash(texto []byte) {
  // MD5
  hashMD5 := md5.Sum(texto)
  fmt.Printf("%x", hashMD5)

  // SHA1
  hashSHA1 := sha1.Sum(texto)
  fmt.Printf("%x", hashSHA1)
  
  // SHA256
  hashSHA256 := sha256.Sum256(texto)
  fmt.Printf("%x", hashSHA256)
  
  //sha512
  hashSHA512 := sha512.Sum512_256(texto)
  fmt.Printf("%x", hashSHA512)
}
```



## Rascunho de canais de comunicação


site
https://tio.dev

github
https://github.com/tio-dev

dev_to
https://dev.to/tiodev

replit
https://replit.com/@tio-dev

twitter
https://twitter.com/richard_tiodev

youtube
https://www.youtube.com/channel/UC3i9Ma7ZZicOfpzKEbMEXGg


## Rascunho de referências

Vovó Vick - Aldeia Numa Boa (Viktoria Tkotz)
https://web.archive.org/web/20130424042350/http://numaboa.com.br/criptografia

Vovó Vick no Canal YouTube Papo Binário
https://www.youtube.com/watch?v=RDn10qhv0Rw&t=374s
https://www.youtube.com/watch?v=KcF2jxIeBT0&t=505s
https://www.youtube.com/watch?v=MrifsixfNH0&t=1892s

Apostila de Criptografia Divertida
http://www.mat.ufpb.br/bienalsbm/arquivos/Oficinas/PedroMalagutti-TemasInterdisciplinares/Aprendendo_Criptologia_de_Forma_Divertida_Final.pdf

Introdução a Criptografia pelo Fábio Akita

Parte 1/2
https://www.youtube.com/watch?v=CcU5Kc_FN_4

Parte 2/2
https://www.youtube.com/watch?v=HCHqtpipwu4


## Rascunho de recursos de identidade áudio visual

Toquinho - O Pato
https://www.youtube.com/watch?v=z8-yWOXXJ4Y


