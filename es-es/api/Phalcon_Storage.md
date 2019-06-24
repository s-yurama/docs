---
layout: default
language: 'es-es'
version: '4.0'
title: 'Phalcon\Storage'
---

* [Phalcon\Storage\Adapter\AbstractAdapter](#Storage_Adapter_AbstractAdapter)
* [Phalcon\Storage\Adapter\AdapterInterface](#Storage_Adapter_AdapterInterface)
* [Phalcon\Storage\Adapter\Apcu](#Storage_Adapter_Apcu)
* [Phalcon\Storage\Adapter\Libmemcached](#Storage_Adapter_Libmemcached)
* [Phalcon\Storage\Adapter\Memory](#Storage_Adapter_Memory)
* [Phalcon\Storage\Adapter\Redis](#Storage_Adapter_Redis)
* [Phalcon\Storage\Adapter\Stream](#Storage_Adapter_Stream)
* [Phalcon\Storage\AdapterFactory](#Storage_AdapterFactory)
* [Phalcon\Storage\Exception](#Storage_Exception)
* [Phalcon\Storage\Serializer\AbstractSerializer](#Storage_Serializer_AbstractSerializer)
* [Phalcon\Storage\Serializer\Base64](#Storage_Serializer_Base64)
* [Phalcon\Storage\Serializer\Igbinary](#Storage_Serializer_Igbinary)
* [Phalcon\Storage\Serializer\Json](#Storage_Serializer_Json)
* [Phalcon\Storage\Serializer\Msgpack](#Storage_Serializer_Msgpack)
* [Phalcon\Storage\Serializer\None](#Storage_Serializer_None)
* [Phalcon\Storage\Serializer\Php](#Storage_Serializer_Php)
* [Phalcon\Storage\Serializer\SerializerInterface](#Storage_Serializer_SerializerInterface)
* [Phalcon\Storage\SerializerFactory](#Storage_SerializerFactory)

<h1 id="Storage_Adapter_AbstractAdapter">Abstract Class Phalcon\Storage\Adapter\AbstractAdapter</h1>

[Código fuente en GitHub](https://github.com/phalcon/cphalcon/tree/v{{ page.version }}.0/phalcon/storage/adapter/abstractadapter.zep)

| Namespace | Phalcon\Storage\Adapter | | Uses | DateInterval, Phalcon\Helper\Arr, Phalcon\Storage\Adapter\AdapterInterface, Phalcon\Storage\Exception, Phalcon\Storage\SerializerFactory, Phalcon\Storage\Serializer\SerializerInterface | | Implements | AdapterInterface |

This file is part of the Phalcon Framework.

(c) Phalcon Team <team@phalconphp.com>

For the full copyright and license information, please view the LICENSE.txt file that was distributed with this source code.

## Properties

```php
/**
 * @var mixed
 */
protected adapter;

/**
 * Name of the default serializer class
 *
 * @var string
 */
protected defaultSerializer = Php;

/**
 * Name of the default TTL (time to live)
 *
 * @var int
 */
protected lifetime = 3600;

/**
 * @var string
 */
protected prefix = ;

/**
 * Serializer
 *
 * @var <SerializerInterface>
 */
protected serializer;

/**
 * Serializer Factory
 *
 * @var <SerializerFactory>
 */
protected serializerFactory;

```

## Métodos

```php
protected function __construct( mixed $factory, array $options ): void;
```

Sets parameters based on options

```php
abstract public function clear(): bool;
```

Flushes/clears the cache

```php
abstract public function decrement( string $key, int $value = 1 ): int | bool;
```

Decrements a stored number

```php
abstract public function delete( string $key ): bool;
```

Deletes data from the adapter

```php
abstract public function get( string $key ): mixed;
```

Reads data from the adapter

```php
abstract public function getAdapter(): mixed;
```

Returns the adapter - connects to the storage if not connected

```php
public function getDefaultSerializer(): string
```

```php
abstract public function getKeys(): array;
```

Returns all the keys stored

```php
public function getPrefix(): string
```

```php
abstract public function has( string $key ): bool;
```

Checks if an element exists in the cache

```php
abstract public function increment( string $key, int $value = 1 ): int | bool;
```

Increments a stored number

```php
abstract public function set( string $key, mixed $value, mixed $ttl ): bool;
```

Stores data in the adapter

```php
public function setDefaultSerializer( string $defaultSerializer )
```

```php
protected function getPrefixedKey( mixed $key ): string;
```

Returns the key requested, prefixed

```php
protected function getSerializedData( mixed $content ): mixed;
```

Returns serialized data

```php
protected function getTtl( mixed $ttl ): int;
```

Calculates the TTL for a cache item

@param DateInterval|int|null $ttl

@return int @throws Exception

```php
protected function getUnserializedData( mixed $content, mixed $defaultValue ): mixed;
```

Returns unserialized data

```php
protected function initSerializer(): void;
```

Initializes the serializer

<h1 id="Storage_Adapter_AdapterInterface">Interface Phalcon\Storage\Adapter\AdapterInterface</h1>

[Código fuente en GitHub](https://github.com/phalcon/cphalcon/tree/v{{ page.version }}.0/phalcon/storage/adapter/adapterinterface.zep)

| Namespace | Phalcon\Storage\Adapter | | Uses | Phalcon\Storage\Serializer\SerializerInterface |

Interface for Phalcon\Logger adapters

## Métodos

```php
public function clear(): bool;
```

Flushes/clears the cache

```php
public function decrement( string $key, int $value = 1 ): int | bool;
```

Decrements a stored number

```php
public function delete( string $key ): bool;
```

Deletes data from the adapter

```php
public function get( string $key ): mixed;
```

Reads data from the adapter

```php
public function getAdapter(): mixed;
```

Returns the already connected adapter or connects to the backend server(s)

```php
public function getKeys(): array;
```

Returns all the keys stored

```php
public function getPrefix(): string;
```

Returns the prefix for the keys

```php
public function has( string $key ): bool;
```

Checks if an element exists in the cache

```php
public function increment( string $key, int $value = 1 ): int | bool;
```

Increments a stored number

```php
public function set( string $key, mixed $value, mixed $ttl ): bool;
```

Stores data in the adapter

<h1 id="Storage_Adapter_Apcu">Class Phalcon\Storage\Adapter\Apcu</h1>

[Código fuente en GitHub](https://github.com/phalcon/cphalcon/tree/v{{ page.version }}.0/phalcon/storage/adapter/apcu.zep)

| Namespace | Phalcon\Storage\Adapter | | Uses | Phalcon\Helper\Arr, Phalcon\Storage\Adapter\AbstractAdapter, Phalcon\Storage\Exception, Phalcon\Storage\SerializerFactory, Phalcon\Storage\Serializer\SerializerInterface | | Extends | AbstractAdapter |

Apcu adapter

## Properties

```php
/**
 * @var array
 */
protected options;

```

## Métodos

```php
public function __construct( mixed $factory, array $options );
```

Constructor

```php
public function clear(): bool;
```

Flushes/clears the cache

```php
public function decrement( string $key, int $value = 1 ): int | bool;
```

Decrements a stored number

@param string $key @param int $value

@return bool|int

```php
public function delete( string $key ): bool;
```

Reads data from the adapter

@param string $key

@return bool

```php
public function get( string $key, mixed $defaultValue ): mixed;
```

Reads data from the adapter

@param string $key @param null $defaultValue

@return mixed

```php
public function getAdapter(): mixed;
```

Returns the already connected adapter or connects to the Memcached server(s)

@return mixed

```php
public function getKeys(): array;
```

Stores data in the adapter

@return array

```php
public function has( string $key ): bool;
```

Checks if an element exists in the cache

@param string $key

@return bool

```php
public function increment( string $key, int $value = 1 ): int | bool;
```

Increments a stored number

@param string $key @param int $value

@return bool|int

```php
public function set( string $key, mixed $value, mixed $ttl ): bool;
```

Stores data in the adapter

@param string $key @param mixed $value @param null $ttl

@return bool @throws \Exception

<h1 id="Storage_Adapter_Libmemcached">Class Phalcon\Storage\Adapter\Libmemcached</h1>

[Código fuente en GitHub](https://github.com/phalcon/cphalcon/tree/v{{ page.version }}.0/phalcon/storage/adapter/libmemcached.zep)

| Namespace | Phalcon\Storage\Adapter | | Uses | Phalcon\Helper\Arr, Phalcon\Storage\Adapter\AbstractAdapter, Phalcon\Storage\Exception, Phalcon\Storage\SerializerFactory, Phalcon\Storage\Serializer\SerializerInterface | | Extends | AbstractAdapter |

Libmemcached adapter

## Properties

```php
/**
 * @var array
 */
protected options;

```

## Métodos

```php
public function __construct( mixed $factory, array $options );
```

Libmemcached constructor.

@param array $options

```php
public function clear(): bool;
```

Flushes/clears the cache

@return bool @throws Exception

```php
public function decrement( string $key, int $value = 1 ): int | bool;
```

Decrements a stored number

```php
public function delete( string $key ): bool;
```

Reads data from the adapter

@param string $key

@return bool @throws Exception

```php
public function get( string $key, mixed $defaultValue ): mixed;
```

Reads data from the adapter

@param string $key @param null $defaultValue

@return mixed @throws Exception

```php
public function getAdapter(): mixed;
```

Returns the already connected adapter or connects to the Memcached server(s)

@return Memcached @throws Exception

```php
public function getKeys(): array;
```

Stores data in the adapter

@return array @throws Exception

```php
public function has( string $key ): bool;
```

Checks if an element exists in the cache

@param string $key

@return bool @throws Exception

```php
public function increment( string $key, int $value = 1 ): int | bool;
```

Increments a stored number

@param string $key @param int $value

@return bool|int @throws Exception

```php
public function set( string $key, mixed $value, mixed $ttl ): bool;
```

Stores data in the adapter

@param string $key @param mixed $value @param null $ttl

@return bool @throws Exception

<h1 id="Storage_Adapter_Memory">Class Phalcon\Storage\Adapter\Memory</h1>

[Código fuente en GitHub](https://github.com/phalcon/cphalcon/tree/v{{ page.version }}.0/phalcon/storage/adapter/memory.zep)

| Namespace | Phalcon\Storage\Adapter | | Uses | Phalcon\Collection\Collection, Phalcon\Helper\Arr, Phalcon\Storage\Adapter\AbstractAdapter, Phalcon\Storage\Exception, Phalcon\Storage\SerializerFactory, Phalcon\Storage\Serializer\SerializerInterface | | Extends | AbstractAdapter |

Memory adapter

## Properties

```php
/**
 * @var Collection
 */
protected data;

/**
 * @var array
 */
protected options;

```

## Métodos

```php
public function __construct( mixed $factory, array $options );
```

Constructor

```php
public function clear(): bool;
```

Flushes/clears the cache

```php
public function decrement( string $key, int $value = 1 ): int | bool;
```

Decrements a stored number

@param string $key @param int $value

@return bool|int

```php
public function delete( string $key ): bool;
```

Reads data from the adapter

@param string $key

@return bool

```php
public function get( string $key, mixed $defaultValue ): mixed;
```

Reads data from the adapter

@param string $key @param mixed|null $defaultValue

@return mixed

```php
public function getAdapter(): mixed;
```

Returns the already connected adapter or connects to the Memcached server(s)

@return mixed

```php
public function getKeys(): array;
```

Stores data in the adapter

@return array

```php
public function has( string $key ): bool;
```

Checks if an element exists in the cache

@param string $key

@return bool

```php
public function increment( string $key, int $value = 1 ): int | bool;
```

Increments a stored number

@param string $key @param int $value

@return bool|int

```php
public function set( string $key, mixed $value, mixed $ttl ): bool;
```

Stores data in the adapter

@param string $key @param mixed $value @param null $ttl

@return bool

<h1 id="Storage_Adapter_Redis">Class Phalcon\Storage\Adapter\Redis</h1>

[Código fuente en GitHub](https://github.com/phalcon/cphalcon/tree/v{{ page.version }}.0/phalcon/storage/adapter/redis.zep)

| Namespace | Phalcon\Storage\Adapter | | Uses | Phalcon\Helper\Arr, Phalcon\Storage\Adapter\AbstractAdapter, Phalcon\Storage\Exception, Phalcon\Storage\SerializerFactory, Phalcon\Storage\Serializer\SerializerInterface | | Extends | AbstractAdapter |

Redis adapter

## Properties

```php
/**
 * @var array
 */
protected options;

```

## Métodos

```php
public function __construct( mixed $factory, array $options );
```

Constructor

```php
public function clear(): bool;
```

Flushes/clears the cache

@return bool @throws Exception

```php
public function decrement( string $key, int $value = 1 ): int | bool;
```

Decrements a stored number

@param string $key @param int $value

@return bool|int @throws Exception

```php
public function delete( string $key ): bool;
```

Reads data from the adapter

@param string $key

@return bool @throws Exception

```php
public function get( string $key, mixed $defaultValue ): mixed;
```

Reads data from the adapter

@param string $key @param null $defaultValue

@return mixed @throws Exception

```php
public function getAdapter(): mixed;
```

Returns the already connected adapter or connects to the Memcached server(s)

@return mixed|\Redis @throws Exception

```php
public function getKeys(): array;
```

Stores data in the adapter

@return array @throws Exception

```php
public function has( string $key ): bool;
```

Checks if an element exists in the cache

@param string $key

@return bool @throws Exception

```php
public function increment( string $key, int $value = 1 ): int | bool;
```

Increments a stored number

@param string $key @param int $value

@return bool|int @throws Exception

```php
public function set( string $key, mixed $value, mixed $ttl ): bool;
```

Stores data in the adapter

@param string $key @param mixed $value @param null $ttl

@return bool @throws Exception

<h1 id="Storage_Adapter_Stream">Class Phalcon\Storage\Adapter\Stream</h1>

[Código fuente en GitHub](https://github.com/phalcon/cphalcon/tree/v{{ page.version }}.0/phalcon/storage/adapter/stream.zep)

| Namespace | Phalcon\Storage\Adapter | | Uses | Phalcon\Helper\Arr, Phalcon\Helper\Str, Phalcon\Storage\Adapter\AbstractAdapter, Phalcon\Storage\Exception, Phalcon\Storage\SerializerFactory, Phalcon\Storage\Serializer\SerializerInterface | | Extends | AbstractAdapter |

Stream adapter

## Properties

```php
/**
    * @var string
    */
protected cacheDir = ;

/**
 * @var array
 */
protected options;

```

## Métodos

```php
public function __construct( mixed $factory, array $options );
```

Stream constructor.

```php
public function clear(): bool;
```

Flushes/clears the cache

```php
public function decrement( string $key, int $value = 1 ): int | bool;
```

Decrements a stored number

```php
public function delete( string $key ): bool;
```

Reads data from the adapter

```php
public function get( string $key, mixed $defaultValue ): mixed;
```

Reads data from the adapter

```php
public function getAdapter(): mixed;
```

Returns the already connected adapter or connects to the Memcached server(s)

```php
public function getKeys(): array;
```

Stores data in the adapter

```php
public function has( string $key ): bool;
```

Checks if an element exists in the cache and is not expired

```php
public function increment( string $key, int $value = 1 ): int | bool;
```

Increments a stored number

```php
public function set( string $key, mixed $value, mixed $ttl ): bool;
```

Stores data in the adapter

<h1 id="Storage_AdapterFactory">Class Phalcon\Storage\AdapterFactory</h1>

[Código fuente en GitHub](https://github.com/phalcon/cphalcon/tree/v{{ page.version }}.0/phalcon/storage/adapterfactory.zep)

| Namespace | Phalcon\Storage | | Uses | Phalcon\Factory\AbstractFactory, Phalcon\Storage\Adapter\AbstractAdapter, Phalcon\Storage\SerializerFactory | | Extends | AbstractFactory |

This file is part of the Phalcon Framework.

(c) Phalcon Team <team@phalconphp.com>

For the full copyright and license information, please view the LICENSE.txt file that was distributed with this source code.

## Properties

```php
/**
 * @var <SerializerFactory>
 */
private serializerFactory;

```

## Métodos

```php
public function __construct( mixed $factory, array $services );
```

AdapterFactory constructor.

```php
public function newInstance( string $name, array $options ): AbstractAdapter;
```

Create a new instance of the adapter

```php
protected function getAdapters(): array;
```

//

<h1 id="Storage_Exception">Class Phalcon\Storage\Exception</h1>

[Código fuente en GitHub](https://github.com/phalcon/cphalcon/tree/v{{ page.version }}.0/phalcon/storage/exception.zep)

| Namespace | Phalcon\Storage | | Extends | \Phalcon\Exception |

Exceptions thrown in Phalcon\Storage will use this class

<h1 id="Storage_Serializer_AbstractSerializer">Abstract Class Phalcon\Storage\Serializer\AbstractSerializer</h1>

[Código fuente en GitHub](https://github.com/phalcon/cphalcon/tree/v{{ page.version }}.0/phalcon/storage/serializer/abstractserializer.zep)

| Namespace | Phalcon\Storage\Serializer | | Uses | Phalcon\Storage\Exception, Phalcon\Storage\Serializer\SerializerInterface | | Implements | SerializerInterface |

This file is part of the Phalcon Framework.

(c) Phalcon Team <team@phalconphp.com>

For the full copyright and license information, please view the LICENSE.txt file that was distributed with this source code.

## Properties

```php
/**
 * @var mixed
 */
protected data;

```

## Métodos

```php
public function __construct( mixed $data ): void;
```

    Constructor
    

```php
public function getData(): mixed
```

```php
public function setData( mixed $data )
```

```php
protected function isSerializable( mixed $data ): bool;
```

If this returns true, then the data returns back as is

<h1 id="Storage_Serializer_Base64">Class Phalcon\Storage\Serializer\Base64</h1>

[Código fuente en GitHub](https://github.com/phalcon/cphalcon/tree/v{{ page.version }}.0/phalcon/storage/serializer/base64.zep)

| Namespace | Phalcon\Storage\Serializer | | Uses | Phalcon\Storage\Serializer\AbstractSerializer | | Extends | AbstractSerializer |

This file is part of the Phalcon Framework.

(c) Phalcon Team <team@phalconphp.com>

For the full copyright and license information, please view the LICENSE.txt file that was distributed with this source code.

## Métodos

```php
public function serialize(): string;
```

    Serializes data
    

```php
public function unserialize( mixed $data ): void;
```

    Unserializes data
    

<h1 id="Storage_Serializer_Igbinary">Class Phalcon\Storage\Serializer\Igbinary</h1>

[Código fuente en GitHub](https://github.com/phalcon/cphalcon/tree/v{{ page.version }}.0/phalcon/storage/serializer/igbinary.zep)

| Namespace | Phalcon\Storage\Serializer | | Uses | Phalcon\Storage\Serializer\AbstractSerializer | | Extends | AbstractSerializer |

This file is part of the Phalcon Framework.

(c) Phalcon Team <team@phalconphp.com>

For the full copyright and license information, please view the LICENSE.txt file that was distributed with this source code.

## Métodos

```php
public function serialize(): string;
```

    Serializes data
    

```php
public function unserialize( mixed $data ): void;
```

    Unserializes data
    

<h1 id="Storage_Serializer_Json">Class Phalcon\Storage\Serializer\Json</h1>

[Código fuente en GitHub](https://github.com/phalcon/cphalcon/tree/v{{ page.version }}.0/phalcon/storage/serializer/json.zep)

| Namespace | Phalcon\Storage\Serializer | | Uses | Phalcon\Storage\Serializer\AbstractSerializer | | Extends | AbstractSerializer |

This file is part of the Phalcon Framework.

(c) Phalcon Team <team@phalconphp.com>

For the full copyright and license information, please view the LICENSE.txt file that was distributed with this source code.

## Métodos

```php
public function serialize(): string;
```

    Serializes data
    

```php
public function unserialize( mixed $data ): void;
```

    Unserializes data
    

<h1 id="Storage_Serializer_Msgpack">Class Phalcon\Storage\Serializer\Msgpack</h1>

[Código fuente en GitHub](https://github.com/phalcon/cphalcon/tree/v{{ page.version }}.0/phalcon/storage/serializer/msgpack.zep)

| Namespace | Phalcon\Storage\Serializer | | Uses | Phalcon\Storage\Serializer\AbstractSerializer | | Extends | AbstractSerializer |

This file is part of the Phalcon Framework.

(c) Phalcon Team <team@phalconphp.com>

For the full copyright and license information, please view the LICENSE.txt file that was distributed with this source code.

## Métodos

```php
public function serialize(): string | null;
```

    Serializes data
    

```php
public function unserialize( mixed $data ): void;
```

    Unserializes data
    

<h1 id="Storage_Serializer_None">Class Phalcon\Storage\Serializer\None</h1>

[Código fuente en GitHub](https://github.com/phalcon/cphalcon/tree/v{{ page.version }}.0/phalcon/storage/serializer/none.zep)

| Namespace | Phalcon\Storage\Serializer | | Uses | Phalcon\Storage\Serializer\AbstractSerializer | | Extends | AbstractSerializer |

This file is part of the Phalcon Framework.

(c) Phalcon Team <team@phalconphp.com>

For the full copyright and license information, please view the LICENSE.txt file that was distributed with this source code.

## Métodos

```php
public function serialize(): string;
```

    Serializes data
    

```php
public function unserialize( mixed $data ): void;
```

    Unserializes data
    

<h1 id="Storage_Serializer_Php">Class Phalcon\Storage\Serializer\Php</h1>

[Código fuente en GitHub](https://github.com/phalcon/cphalcon/tree/v{{ page.version }}.0/phalcon/storage/serializer/php.zep)

| Namespace | Phalcon\Storage\Serializer | | Uses | Phalcon\Storage\Exception, Phalcon\Storage\Serializer\AbstractSerializer | | Extends | AbstractSerializer |

This file is part of the Phalcon Framework.

(c) Phalcon Team <team@phalconphp.com>

For the full copyright and license information, please view the LICENSE.txt file that was distributed with this source code.

## Métodos

```php
public function serialize(): string;
```

    Serializes data
    

```php
public function unserialize( mixed $data ): void;
```

    Unserializes data
    

<h1 id="Storage_Serializer_SerializerInterface">Interface Phalcon\Storage\Serializer\SerializerInterface</h1>

[Código fuente en GitHub](https://github.com/phalcon/cphalcon/tree/v{{ page.version }}.0/phalcon/storage/serializer/serializerinterface.zep)

| Namespace | Phalcon\Storage\Serializer | | Extends | Array |

This file is part of the Phalcon Framework.

(c) Phalcon Team <team@phalconphp.com>

For the full copyright and license information, please view the LICENSE.txt file that was distributed with this source code.

## Métodos

```php
public function getData(): mixed;
```

@var mixed

```php
public function setData( mixed $data ): void;
```

@param $data

<h1 id="Storage_SerializerFactory">Class Phalcon\Storage\SerializerFactory</h1>

[Código fuente en GitHub](https://github.com/phalcon/cphalcon/tree/v{{ page.version }}.0/phalcon/storage/serializerfactory.zep)

| Namespace | Phalcon\Storage | | Uses | Phalcon\Factory\AbstractFactory, Phalcon\Storage\Serializer\SerializerInterface | | Extends | AbstractFactory |

This file is part of the Phalcon Framework.

(c) Phalcon Team <team@phalconphp.com>

For the full copyright and license information, please view the LICENSE.txt file that was distributed with this source code.

## Métodos

```php
public function __construct( array $services );
```

SerializerFactory constructor.

@param array services

```php
public function newInstance( string $name ): SerializerInterface;
```

@param string name

@return mixed @throws Exception

```php
protected function getAdapters(): array;
```

//