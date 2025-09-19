# Subneteo detallado de BR1 LAN (192.168.33.128/25 → /26)

Queremos obtener la subred de BR1 LAN a partir de la red base 192.168.33.128/25.

------------------------------------------------------------
1. Red base
------------------------------------------------------------
- La notación /25 significa que los primeros 25 bits son de red.
- Máscara /25 en decimal: 255.255.255.128
- Máscara /25 en binario:
  11111111.11111111.11111111.10000000

Esto deja:
- 25 bits de red
- 7 bits de host

------------------------------------------------------------
2. Necesidad de BR1 LAN
------------------------------------------------------------
- BR1 LAN necesita una subred con muchos hosts.
- Elegimos /26.

Cálculo de hosts:
- 32 - 26 = 6 bits de host
- 2^6 = 64 direcciones
- 64 - 2 = 62 hosts útiles

------------------------------------------------------------
3. Máscara de /26
------------------------------------------------------------
- Máscara /26 en decimal: 255.255.255.192
- Máscara /26 en binario:
  11111111.11111111.11111111.11000000

En el último octeto:
- 2 bits de red (11)
- 6 bits de host (000000)

------------------------------------------------------------
4. Incremento (block size)
------------------------------------------------------------
Incremento = 256 - último valor de la máscara
- Último valor = 192
- 256 - 192 = 64

Esto significa que las subredes /26 empiezan cada 64 direcciones:
0, 64, 128, 192, ...

------------------------------------------------------------
5. Localizando la subred
------------------------------------------------------------
Dentro del bloque 192.168.33.128/25 (128 a 255), las subredes /26 posibles son:
- 192.168.33.128/26 (128 a 191)
- 192.168.33.192/26 (192 a 255)

Usaremos la primera: 192.168.33.128/26

------------------------------------------------------------
6. Dirección de red, broadcast y rango de hosts
------------------------------------------------------------
- Dirección de red: 192.168.33.128
- Broadcast: 192.168.33.191 (128 + 63)
- Primera usable: 192.168.33.129
- Última usable: 192.168.33.190
- Hosts útiles: 62

------------------------------------------------------------
7. Representación en binario (último octeto)
------------------------------------------------------------
Red .128 → 10000000
Máscara /26 → 11000000

Ejemplos:
- Primer host (.129) → 10000001
- Último host (.190) → 10111110
- Broadcast (.191) → 10111111

------------------------------------------------------------
8. Resumen final
------------------------------------------------------------
- Red: 192.168.33.128/26
- Máscara: 255.255.255.192
- Dirección de red: 192.168.33.128
- Primera usable: 192.168.33.129
- Última usable: 192.168.33.190
- Broadcast: 192.168.33.191
- Hosts útiles: 62
