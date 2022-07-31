FROM ruby:3.1

RUN mkdir /rails-chat-be
ENV APP_ROOT /rails-chat-be
WORKDIR $APP_ROOT

COPY ./backend/Gemfile $APP_ROOT/Gemfile
COPY ./backend/Gemfile.lock $APP_ROOT/Gemfile.lock

RUN bundle config --local set path 'backend/vendor/bundle' \
  && bundle install

COPY . $APP_ROOT

COPY ./backend/entrypoint.sh /usr/bin/
RUN chmod +x /usr/bin/entrypoint.sh
ENTRYPOINT ["entrypoint.sh"]
EXPOSE 3000

# Start the main process.
CMD ["rails", "server", "-b", "0.0.0.0"]