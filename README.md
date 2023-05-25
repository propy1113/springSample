# springSample
ユーザー新規登録アプリ
参考URL：https://medium-company.com/thymeleaf%E3%81%A7post%E3%81%97%E3%81%9F%E3%83%87%E3%83%BC%E3%82%BF%E3%82%92jpa%E3%81%A7%E7%99%BB%E9%8C%B2/

springSampleプロジェクトつまづいたところ

1. サーバー立ち上げ時にエラー
mysqlサーバー側でユーザー権限が付与されていないユーザーでデータベースを操作しようとしていた。

変更ファイル
/springSample/src/main/resources/application.properties

変更前 
spring.datasource.url=jdbc:mysql://localhost/sampledb
spring.datasource.username=root
spring.datasource.password=root
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver

変更後(mysqlサーバーでsampledbuserにsampledbに対するユーザー権限を付与した後に下記内容を変更)
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
spring.datasource.url=jdbc:mysql://localhost:3306/sampledb
spring.datasource.username=sampledbuser
spring.datasource.password=sampledbpass




2. サーバー立ち上げ時にエラー
SpringBoot ver2.5以上の仕様で、下記のコードを記述しないと立ち上げ時にエラーが発生する。

変更ファイル
/springSample/src/main/resources/application.properties

変更前
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
spring.datasource.url=jdbc:mysql://localhost:3306/sampledb
spring.datasource.username=sampledbuser
spring.datasource.password=sampledbpass

変更後
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
spring.datasource.url=jdbc:mysql://localhost:3306/sampledb
spring.datasource.username=sampledbuser
spring.datasource.password=sampledbpass

spring.jpa.defer-datasource-initialization=true

spring.jpa.show-sql=true #この記述はエラーには関係なし
