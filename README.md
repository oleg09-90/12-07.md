# Репликация и масштабирование. Часть 2

**Перваков Олег**

## Решения заданий

### Задание 1
![image](https://github.com/user-attachments/assets/03999cf2-36ee-476f-b2fa-815e85beb7aa)

### Задание 2
![image](https://github.com/user-attachments/assets/0185e537-ee22-4f12-8296-ee48645eba62)

### Задание 3
![image](https://github.com/user-attachments/assets/8bd419a3-ef93-4069-9969-fb41c0004fb9)



# Блок-схема базы данных

```mermaid
graph TD
    subgraph "Users Shard"
        DB1a["DB1a (Users 1-100000)"]
        DB1b["DB1b (Users 100001-200000)"]
    end

    subgraph "Books Shard"
        DB2a["DB2a (Books: Fiction)"]
        DB2b["DB2b (Books: Non-fiction)"]
    end

    subgraph "Stores Shard"
        DB3a["DB3a (Stores: Region 1)"]
        DB3b["DB3b (Stores: Region 2)"]
    end

    DB1a --> DB1aMaster["DB1a Master (Write)"]
    DB1a --> DB1aSlave["DB1a Slave (Read)"]

    DB1b --> DB1bMaster["DB1b Master (Write)"]
    DB1b --> DB1bSlave["DB1b Slave (Read)"]

    DB2a --> DB2aMaster["DB2a Master (Write)"]
    DB2a --> DB2aSlave["DB2a Slave (Read)"]

    DB2b --> DB2bMaster["DB2b Master (Write)"]
    DB2b --> DB2bSlave["DB2b Slave (Read)"]

    DB3a --> DB3aMaster["DB3a Master (Write)"]
    DB3a --> DB3aSlave["DB3a Slave (Read)"]

    DB3b --> DB3bMaster["DB3b Master (Write)"]
    DB3b --> DB3bSlave["DB3b Slave (Read)"]

    DB1aMaster -->|Sync| DB1aSlave
    DB1bMaster -->|Sync| DB1bSlave
    DB2aMaster -->|Sync| DB2aSlave
    DB2bMaster -->|Sync| DB2bSlave
    DB3aMaster -->|Sync| DB3aSlave
    DB3bMaster -->|Sync| DB3bSlave


