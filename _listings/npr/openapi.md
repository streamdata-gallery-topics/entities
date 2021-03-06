swagger: "2.0"
x-collection-name: NPR
x-complete: 1
info:
  title: NPR One API Reference
  description: npr-one-is-a-smart-application-that-brings-the-best-of-npr-and-member-station-programming-newscasts-podcasts-and-stories-together-to-create-a-new-experience-for-listening--it-provides-an-editorcurated-and-localized-mobile-listening-experience-based-on-the-content-the-listener-chooses-likes-shares-and-enjoys--the-api-provides-all-of-the-content-and-customization-in-a-simple-structured-way-that-is-easy-for-applicationdevelopers-to-implement-
  termsOfService: http://dev.npr.org/develop/terms-of-use
  contact:
    name: NPR One Enterprise Team
    url: http://dev.npr.org
    email: NPROneEnterprise@npr.org
  version: 1.0.0
host: api.npr.org
basePath: /
schemes:
- http
produces:
- application/json
consumes:
- application/json
paths:
  /identity/v2/following:
    post:
      summary: Update the following status of the logged-in user for a particular
        aggregation
      description: After a successful call, this returns a User document with an updated
        list of affiliations.
      operationId: postFollowing
      x-api-path-slug: identityv2following-post
      parameters:
      - in: body
        name: body
        description: A JSON-serialized object which contains data about a user affiliation
          such as the aggregation ID, affiliation rating, aggregation URL, days since
          last listen, and following status
        schema:
          $ref: '#/definitions/holder'
      - in: query
        name: No Name
      responses:
        200:
          description: OK
      tags:
      - News
      - Entity
      - Following
  /identity/v2/stations:
    put:
      summary: Update the logged-in user's favorite station(s)
      description: Right now, only the primary station can be changed. Previously
        selected stations will not be deleted, but the new station will be moved to
        first in the array.
      operationId: updateStations
      x-api-path-slug: identityv2stations-put
      parameters:
      - in: body
        name: body
        description: A JSON-serialized array of station IDs
        schema:
          $ref: '#/definitions/holder'
      - in: query
        name: No Name
      responses:
        200:
          description: OK
      tags:
      - News
      - Entity
      - Stations
  /identity/v2/user:
    get:
      summary: Get the latest state information about the logged-in user
      description: After a successful login, the client should send a `GET` call approximately
        once an hour to refresh the user data.
      operationId: getUser
      x-api-path-slug: identityv2user-get
      parameters:
      - in: query
        name: No Name
      responses:
        200:
          description: OK
      tags:
      - News
      - Entity
      - User
  /identity/v2/user/inherit:
    post:
      summary: Copy listening data from a temporary user account to the logged-in
        user's account
      description: |-
        This can and should only be used by clients who have access to the `temporary_user` grant type.
            Third-party developers do not have access to this grant type by default, and will not need this endpoint.
      operationId: inheritFromTempUser
      x-api-path-slug: identityv2userinherit-post
      parameters:
      - in: query
        name: No Name
      - in: query
        name: temp_user
        description: The temporary users ID before the user registered or logged in
      responses:
        200:
          description: OK
      tags:
      - News
      - Entity
      - User
      - Inherit