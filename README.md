> Taller en directo con suscriptores de Web Reactiva para conocer las características principales de Prisma.

![cover-workshop-prisma](https://user-images.githubusercontent.com/1122071/225116136-ee2857f9-9941-42ba-a1a9-259fc413ee9f.png)


ㅤ

## ¿Por qué Prisma?

Prisma es un ORM (Object-Relational Mapping) de código abierto basado en JavaScript/TypeScript que permite a los desarrolladores interactuar con bases de datos de manera más eficiente y segura. Algunas de sus principales características son:

- **Tipado seguro**: Prisma utiliza tipos de datos estáticos para evitar errores de tipo en tiempo de ejecución y mejorar la integridad de los datos.

- **Sintaxis intuitiva**: La sintaxis de Prisma es fácil de leer y escribir, lo que facilita su uso y reduce el tiempo de desarrollo.

- **Generación de consultas eficientes**: Prisma genera consultas SQL optimizadas automáticamente, lo que mejora el rendimiento y reduce la complejidad del código.

- **Migraciones de esquema**: Prisma permite a los desarrolladores modificar el esquema de la base de datos sin tener que escribir código SQL manualmente.

- **Compatibilidad multiplataforma**: Prisma es compatible con varias bases de datos populares, como MySQL, PostgreSQL y SQLite, así como otras noSQL como MongoDB.

👉 [¿Qué es un ORM?](https://www.youtube.com/watch?v=pKawc1UtVcQ) En 7 minutos
ㅤ
👉 [Prisma en 100 segundos](https://www.youtube.com/watch?v=rLRIB6AF2Dg)



## 🔎 Objetivos prácticos
- Dedicar algo más de 60 minutos a aprender las bases de la librería
- Tener la posibilidad de preguntar dudas en directo
- Poner las manos sobre el teclado y sacar medio c\*ulo fuera de la silla

**¿Dónde me apunto?**
Basta con ser suscriptor/a premium de Web Reactiva

ㅤ

## 🛠¿Cómo funciona el taller?

- La sesión es el jueves 16 de Marzo de 2023 a las 19:00 CET
- El ponente (Dani) irá explicando conceptos y proponiendo ejercicios que estarán en este repositorio
- Cada asistente podrá resolverlos en su propio ordenador.
- Es OBLIGADO tener a punto los requisitos para empezar el taller (leer aquí abajo)
- Realizaremos ejercicios prácticos, en este caso no construiremos una aplicación completa
ㅤ

## 📚 ¿Qué temas va a tener?

1. Sintaxis básica del ORM
2. Cliente para realizar consultas
3. Migraciones
ㅤ

ㅤ

## ✅ Requisitos para empezar el taller

Para ser más ágiles te propongo unos sencillos pasos para tener todo a punto en tu ordenador antes de comenzar el taller.

⏰ 15 minutos.

> Prisma trabaja sobre JavaScript o TypeScript con lo que es conveniente tener conocimientos de uno de estos lenguajes. También conviene tener conocimientos básicos de bases de datos.

ㅤ
ㅤ


### 1. Editor de código

Usaremos Visual Studio Code para la explicación.

- [Extensión oficial de Prisma](https://marketplace.visualstudio.com/items?itemName=Prisma.prisma)

👉 Prisma tiene un [Playground](https://playground.prisma.io/) que no es 100% configurable pero puede ayudarte en el aprendizaje.

👀 Cuenta con una extensa colección de ejemplos en [prisma-examples](https://github.com/prisma/prisma-examples)

ㅤ
ㅤ


### 2. Una base de datos lista

En cualquiera de las alternativas:

- Comprueba que la base de datos es accesible (para no tener problemas con permisos, certificados…)
- 👀 Ten las credenciales listas para los siguientes pasos

Aquí tenemos varias alternativas:

**A. Opción cómoda**

Si tu sistema es compatible con SQLite, no tendrás que hacer nada ya que Prisma podrá encargarse por ti de generar la base de datos.


**B. Opción pro**

Si te es fácil crear una base de datos en local, hazlo antes de la sesión y comprueba que tienes todo listo.

Recomendamos PostgreSQL o MySQL (MariaDB). MongoDB no va a ser el objetivo de este taller, por lo que no te recomiendo usarlo.



👉 Lista completa de [bases de datos soportadas](https://www.prisma.io/docs/reference/database-reference/supported-databases)

**C. Opción nube**

Puedes crear una base de datos Postgres de forma gratuita y en la nube en servicios como [Railway](https://railway.app/) o [Supabase](https://supabase.com).

ㅤ


### 3. Crea el proyecto

Creamos el proyecto con el código mínimo para tenerlo todo funcionando.

```bash
mkdir workshop-prisma
cd workshop-prisma
```

Inicializamos el proyecto:

```bash
npm init -y
npm install ts-node @types/node --save-dev
```

👉 Usaremos TypeScript, si no lo tienes instalado globalmente (`tsc`) hazlo en el proyecto con `npm install typescript --save-dev `.

Inicializamos TypeScript:

```bash
npx tsc --init
```

Instalamos el Prisma Client:

```bash
npm install --save-dev @prisma/client
```

ㅤ

### 4. Inicializando Prisma

Ahora inicializamos el `schema` de Prisma.

Atento a este paso:

1) Si vas a usar SQLite

```bash
npx prisma init --datasource-provider sqlite
```

2) Con cualquier otro proveedor, adapta el comando (en este ejemplo MySQL)

```bash
npx prisma init --datasource-provider mysql
```

Esto creará dos cosas:

- Un fichero en `prisma/schema.prisma` donde estarán nuestra configuración de Prisma
- Un fichero `.env` donde aparece la variable `DATABASE\_URL`. Si has optado por la opción 2 debes completar la información de acceso en ese lugar. ([Ayuda](https://www.prisma.io/docs/guides/development-environment/environment-variables#example-set-the-database_url-environment-variable-in-an-env-file))

Por último vamos a comprobar que todo funciona:

Añade estas lineas al final de `prisma/schema.prisma`

```bash
model User {
  id    Int     @id @default(autoincrement())
  email String  @unique
  name  String?
}
```

En consola ejecuta esto:

`npx prisma generate`


Y luego la migración (ya veremos que es esto) para que se genere en tu base de datos tablas y campos:

`npx prisma migrate dev --name init`

Si ha ido todo bien tendrás este mensaje en pantalla:

```bash
Environment variables loaded from .env
Prisma schema loaded from prisma/schema.prisma
Datasource "db": SQLite database "dev.db" at "file:./dev.db"

Applying migration `20230314194438_init`

The following migration(s) have been created and applied from new schema changes:
```





**¡Estas listoa para empezar!** 🥳
