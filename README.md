# Biblioteca Sui
Biblioteca es un módulo desarrollado en Move para la blockchain Sui, que permite gestionar una colección de libros de forma descentralizada.

Con este contrato inteligente podrás crear bibliotecas, agregar, actualizar y eliminar libros, así como administrar su disponibilidad, todo con persistencia y verificación de datos en la red.

## Pasos para desplegar en testnet:
1. Contar con tu entorno de Sui client configurando, puedes ver el tutorial en el repositorio de [first steps](https://github.com/Zona-Tres/sui-first-steps/tree/main/extras/sui_client).

2. Posicionarte en la carpeta raiz del proyecto donde tienes el código desarrollado.

3. Hacer el build del código mediante: `sui client build`

**Nota**: Si el buld falla es posiblemente porque el código tenga errores de sintaxis. Para verificarlo antes puedes hacer: `sui move test`.

4. Hacer el push del proyecto a la testnet com: `sui client publish --gas-budget 100000000`

5. Y listo!!!, ya tienes tu proyecto desplegado en la testnet. Como resultado obtendras varios logs, puedes ver el id (`OBJECT-ID`) del paquete en `OBJECT CHANGES` que se encuentra en `PUBLISHED OBJECTS`.

6. Interactua con el paquete. Para ello es necesario usar la siguiente estructura:

```
sui client call --package ID-DEL-PAQUETE --module biblioteca --function NOMBRE-DE-LA-FUNCION --args ARGUENTOS(Si es que la funcion los tiene)
```


## Funciones del módulo 
1. `crear_biblioteca`

**Descripción**: Crea una nueva biblioteca vacía y la transfiere al creador de la transacción.

---
2. `agregar_libro`

**Descripción**: Agrega un nuevo libro a la biblioteca, validando que el ID no exista previamente.

**Argumentos**:

``biblioteca``: Referencia mutable a la biblioteca.

``identificador``: ID único para el libro.

``titulo``: Título del libro.

``autor``: Autor del libro.

`publicado`: Año de publicación.

`disponible`: Estado de disponibilidad (true/false).

---

3. `actualizar_titulo`

**Descripción**: Cambia el título de un libro existente.

**Argumentos**:

`biblioteca`: Referencia mutable a la biblioteca.

`identificador`: ID del libro a actualizar.

`titulo`: Nuevo título del libro.

---

4. **actualizar_autor**

**Descripción**: Cambia el autor de un libro existente.

**Argumentos**:

`biblioteca`: Referencia mutable a la biblioteca.

`identificador`: ID del libro a actualizar.

`autor`: Nuevo autor del libro.

---

5. **actualizar_publicado**

**Descripción**: Actualiza el año de publicación de un libro.

**Argumentos**:

`biblioteca`: Referencia mutable a la biblioteca.

`identificador`: ID del libro a actualizar.

`publicado`: Nuevo año de publicación.

---

6. `actualizar_disponibilidad`

**Descripción**: Cambia si un libro está disponible o no.

**Argumentos**:

`biblioteca`: Referencia mutable a la biblioteca.

`identificador`: ID del libro a actualizar.

`disponible`: Nuevo estado de disponibilidad (true/false).

---

7. `borrar_libro`

**Descripción**: Elimina un libro de la biblioteca.

**Argumentos**:

`biblioteca`: Referencia mutable a la biblioteca.

`identificador`: ID del libro a eliminar.

---

8. `eliminar_biblioteca`

**Descripción**: Elimina toda la biblioteca de la blockchain.

**Argumentos**:

`biblioteca`: Biblioteca a eliminar.

